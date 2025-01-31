So its ubua texturepacks librari
description "Freds minimal Nixos configuration flake.";

inputs

nixpkgs.urlithub NixOS/nixpkgs/nixpkgs-unstable

nixpkgs.follows "nixos-cosmic/nixpkgs"; # NOTE: change "nixpkgs" to "nixpkgs-stable" to use stable NixOS release

nixos-cosmic.url "github:lilyinstarlight/nixos-cosmic";

};

outputs { self, nixpkgs, nixos-cosmic,... inputs: {

nixosConfigurations. T14s nixpkgs.lib.nixosSystem {

specialArgs (inherit inputs; };

system "x86_64-linux";

modules = [

(import./configuration.nix)

nix.settings = {

substituters = [ "https://cosmic.cachix.org/" ];

trusted-public-keys ["cosmic.cachix.org-1:Dya9IyXD4xdBehWjrkPv6rtxpmMdRel@2smYzA85dPE=" ];

};

nixos-cosmic.nixosModules.default

11

}