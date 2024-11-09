
# 🚀  Rust Weather App

[![][ci_shield]](https://github.com/chrohangurjar1/RustWeatherApp/actions/workflows/ci.yml?query=branch%3Amain)
[![][last_commit_shield]](https://github.com/chrohangurjar1/RustWeatherApp/commits/main)
[![][crates_io_shield]](https://crates.io/crates/RustWeatherApp)
[![][msrv_shield]](https://github.com/chrohangurjar1/RustWeatherApp)

<div align="center">

[![][preview]][preview]

</div>

`RustWeatherApp` lives in your terminal and her passion is meteorology.

If you spend time in the TUI, you'll have a little companion nearby who knows about the weather.

## Contents

- [How to use?](https://github.com/chrohangurjar1/RustWeatherApp#how-to-use)
- [Showcase](https://github.com/chrohangurjar1/RustWeatherApp#showcase)
- [Config](https://github.com/chrohangurjar1/RustWeatherApp#config)
- [Installation](https://github.com/chrohangurjar1/RustWeatherApp#installation)
- [Outlook](https://github.com/chrohangurjar1/RustWeatherApp#outlook)
- [Credits](https://github.com/chrohangurjar1/RustWeatherApp#credits)

## How to use?

**Just call**

```
RustWeatherApp
```

Without having added an address or options, RustWeatherApp uses the [config](https://github.com/chrohangurjar1/RustWeatherApp#config) saved as default.<br>
If you haven't configured anything as default yet, RustWeatherApp can try to search for a weather station near you and save the searched location as default.

**It's always possible to specify an address.** E.g.,

```
RustWeatherApp melbourne
```

Depending on the place you are looking for, you might need to be more specific.
For example, the above call will get Melbourne in Australia. If you are aiming for Melbourne in the US, ask for `melbourne,florida`.
If the address contains spaces, separate them with a hyphen or enclose them in quotation marks (e.g., `new-york` or `"new york"`).

To search explicitly for a weather station in the vicinity, call

```
RustWeatherApp auto
```

As a final example, we instruct RustWeatherApp to use Fahrenheit and mph as units and add the hourly forecast for the day

```
RustWeatherApp -u f,mph -f d
```

### Find further usage parameters in the help information

```
> RustWeatherApp -h

Usage: RustWeatherApp [OPTIONS] [ADDRESS]

Arguments:
  [ADDRESS]
          Address to check the weather

Options:
  -f, --forecast <FORECAST,...>
          [e.g.: -f w,d] [possible values: disable, (w)eek, to(d)ay, (t)omorrow, mo, tu, we, th, fr, sa, su]
  -F, --historical-weather <%Y-%m-%d,...>
          [e.g.: -F 2021-12-31]
  -u, --units <UNIT,...>
          [e.g.: -u f,12h,in] [possible values: (c)elsius, (f)ahrenheit, kmh, mph, (kn)ots, ms, 12h, 24h, %, mm, (in)ch]
  -l, --language <LANGUAGE>
          Output language [e.g.: en_US]
  -s, --save
          Save the supplied values as default
  -r, --reset
          Wipe RustWeatherApp's configuration data
  -h, --help
          Print help
  -V, --version
          Print version
```

## Showcase

|                                         |                                         |
| :-------------------------------------: | :-------------------------------------: |
|              **First Run**              |           **Hourly Forecast**           |
|       [![][first_run]][first_run]       | [![][hourly_forecast]][hourly_forecast] |
|            **Week Forecast**            |          **\*Terminal Colors**          |
| [![][weekly_forecast]][weekly_forecast] | [![][terminal_colors]][terminal_colors] |
|                                         |                                         |

<sup>\*Rendering and colors are influenced by the terminal used and its theme and font.<br>
E.g., the first of the above screenshots show RustWeatherApp in nvim(toggleterm) using kitty as terminal with a Dracula theme and JetBrainsMono Nerd font. The last screenshot shows RustWeatherApp in Yakuake/Konsole, also with a Dracula color scheme.</sup>

## Config

The address, units and default forecast can be saved as default values in RustWeatherApp's config file by adding the `-s` flag to a run. This will save the config in `RustWeatherApp.ron`.

**Platform locations:**<br>
Lin: `~/.config/weathercrab/`<br>
Mac: `~/Library/Application Support/weathercrab/`<br>
Win: `%USERPROFILE%\AppData\Roaming\weathercrab\`

**Default values**

```rust
(
    address: "", // Address to check the weather, e.g.: "Berlin,DE"
    language: "en_US", // Language code of the output language
    forecast: [], // Forecast to display without adding the `-f` option: `[day]` | `[week]` | `[day, week]`
    units: (
        temperature: celsius, // Temperature units: `celsius` | `fahrenheit`
        speed: kmh, // (Wind)speed units: `kmh` | `mph` | `knots` | `ms`
        time: military, // Time Format: `military` | `am_pm`
        precipitation: probability, // Precipitation units: `probability` | `mm` | `inch`
    ),
    gui: (
        border: rounded, // Border style: `rounded` | `single` | `solid` | `double`
        color: default, // Color: `default` | `plain`
        graph: (
            // Graph style: lines(solid) | lines(slim) | lines(dotted) | dotted | custom((char; 8))
            // `custom` takes exactly 8 chars. E.g. using a set of 4 chars: `custom(('⡀','⡀','⠄','⠄','⠂','⠂','⠁','⠁'))`,
            style: lines(solid),
            rowspan: double, // Graph height: `double` | `single`
            time_indicator: true, // Indication of the current time in the graph: `true` | `false`
        ),
        greeting: true, // Display greeting message: `true` | `false`
    ),
)
```

## Installation

Use rusts package manager to install RustWeatherApp.

**From crates.io**

|             |                       |
| ----------- | --------------------- |
| **Version** | **Command**           |
| release     | `cargo install RustWeatherApp` |
|             |                       |
| development | _not available_       |
|             |                       |

**From git source**

|             |                                                                                   |
| ----------- | --------------------------------------------------------------------------------- |
| **Version** | **Command**                                                                       |
| release     | `cargo install --git https://github.com/chrohangurjar1/RustWeatherApp --tag v1.1.1` |
|             |                                                                                   |
| development | `cargo install --git https://github.com/chrohangurjar1/RustWeatherApp`              |
|             |                                                                                   |

**Requirements and alternative, platform-specific installation instructions can be found in [`INSTALL.md`](https://github.com/chrohangurjar1/RustWeatherApp/blob/main/INSTALL.md).**

> **Important**
> To display symbols correctly, the used terminal must be configured to use a NerdFont.

## Outlook

The [issues](https://github.com/chrohangurjar1/RustWeatherApp/issues) section lists some of the features that are being worked on.

Contributions like 🐛bug reports, ⭐️stars and 💡suggestions are welcome alike!

A simple changelog can be found on the [releases page](https://github.com/chrohangurjar1/RustWeatherApp/releases).

## Contributors

<a href="https://github.com/chrohangurjar1/RustWeatherApp/graphs/contributors">
  <img height='48' src="https://contrib.rocks/image?repo=chrohangurjar1/RustWeatherApp&columns=24" />
</a>

## Credits

- The app uses the open-source weather API for non-commercial use provided by [Open Meteo](https://open-meteo.com/en)

<br>

<!-- Images -->

[preview]: https://github.com/chrohangurjar1/RustWeatherApp/assets/34311583/58780205-816b-4cfd-95f8-9453e754eb94
[crates_io_shield]: https://img.shields.io/crates/v/RustWeatherApp.svg
[last_commit_shield]: https://img.shields.io/github/last-commit/chrohangurjar1/RustWeatherApp/main.svg
[ci_shield]: https://img.shields.io/github/workflow
