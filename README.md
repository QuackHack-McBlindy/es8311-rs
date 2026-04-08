# **es8311-rs**
 
[![Sponsors](https://img.shields.io/github/sponsors/QuackHack-McBlindy?logo=githubsponsors&label=Sponsor&style=flat&labelColor=ff1493&logoColor=fff&color=rgba(234,74,170,0.5) "")](https://github.com/sponsors/QuackHack-McBlindy) [![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-Sponsor?style=flat&logo=buymeacoffee&logoColor=fff&labelColor=ff1493&color=ff1493)](https://buymeacoffee.com/quackhackmcblindy)


no_std ES8311 audio codec library.  


## **Installation**

  
Add **es8311** as a dependency in `Cargo.toml`.

```toml
[dependencies]
es8311 = "0.1.0"
```
  


<br>

## **Example usage**

```rust
use es8311::{Es8311, ClockConfig, Resolution, MicGain, Fade};
use esp_hal::i2c::I2c;
use esp_hal::delay::Delay;

let mut i2c = I2c::new(...);
let mut delay = Delay::new();

let codec = Es8311::new(0x10);
let clk_cfg = ClockConfig {
    mclk_inverted: false,
    sclk_inverted: false,
    mclk_from_mclk_pin: true,
    mclk_frequency: 12_288_000,   // 12.288 MHz
    sample_frequency: 48_000,
};

codec.init(&mut i2c, &mut delay, &clk_cfg, Resolution::Bits16, Resolution::Bits16).unwrap();
codec.microphone_config(&mut i2c, false).unwrap();
codec.microphone_gain_set(&mut i2c, MicGain::Gain24dB).unwrap();
codec.volume_set(&mut i2c, 80, None).unwrap();
codec.mute(&mut i2c, false).unwrap();
```

## **Features**

- `defmt` – enables logging in register_dump and other debug output.  


<br><br>

## ☕

[![Sponsors](https://img.shields.io/github/sponsors/QuackHack-McBlindy?logo=githubsponsors&label=Sponsor&style=flat&labelColor=ff1493&logoColor=fff&color=rgba(234,74,170,0.5) "")](https://github.com/sponsors/QuackHack-McBlindy) [![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-Sponsor?style=flat&logo=buymeacoffee&logoColor=fff&labelColor=ff1493&color=ff1493)](https://buymeacoffee.com/quackhackmcblindy)
> Like my work?   
> Buy me a coffee, or become a sponsor.  
> Thanks for supporting open source!    

₿ *Donate crypto? Wallet:* `pungkula.x` 
<a href="https://www.buymeacoffee.com/quackhackmcblindy" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

## **Lisence**

**MIT**  
<br>
