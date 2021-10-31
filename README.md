# Disclaimer

This repository is a fork from https://github.com/Kangie/sddm-sugar-candy.
It only exists for my needs and was not created for any form of profit.

# Installation

Enable `sddm` in your `configuration.nix` and add something like this
```nix
sddm-candy-sugar = stdenv.mkDerivation rec {
    pname = "sddm-candy-sugar-theme";
    version = "2.1";
    dontBuild = true;
    installPhase = ''
      mkdir -p $out/share/sddm/themes
      echo ============================================
      echo $out
      echo ============================================
      cp -aR $src $out/share/sddm/themes/candy-sugar
      ls -la $out/share/sddm/themes
    '';
    src = fetchFromGitHub {
      owner = "Cobaltarena";
      repo = "sddm-theme";
      rev = "f19cf8789736a282d3bce06c35d14c6e4a270a31";
      sha256 = "Taj2ns/vXZiS2uOkPHxvRCjbMtgF/5DueNI9zPtwJ/Q=";
    };
  };
```

Then do `sudo nixos-rebuild switch` and you should be good with this !

# Testing

In your favorite terminal, do `sddm-greeter --test-mode --theme $out/share/sddm/themes/candy-sugar` after installing and replacing `$out` to the right /nix/store path
