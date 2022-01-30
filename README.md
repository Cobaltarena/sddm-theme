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
      rev = "xxxxxxx"; # hash of the commit
      sha256 = "yyyyyyy"; # sha of the repository, can be found using nix-prefetch-github
    };
  };
```

Then do `sudo nixos-rebuild switch` and you should be good with this !

# Testing

In your favorite terminal, do `sddm-greeter --test-mode --theme $out/share/sddm/themes/candy-sugar` after installing and replacing `$out` to the right /nix/store path

# Background

If you want to change the background image, you just have to change the line `Background` property in `theme.conf`
