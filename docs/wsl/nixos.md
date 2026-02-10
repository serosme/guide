# NixOS

## 参考文档

[NixOS-WSL](https://github.com/nix-community/NixOS-WSL)

[NixOS-WSL Documentation](https://nix-community.github.io/NixOS-WSL/)

[nix-channels](https://channels.nixos.org/)

## 命令

安装 NixOS

```shell
wsl --install --from-file nixos.wsl
```

```shell
sudo nix-channel --update
```

```shell
sudo nixos-rebuild switch
```

vim /etc/nixos/configuration.nix

```nixos
  environment.systemPackages = [
    pkgs.vim
    pkgs.git
    pkgs.wget
    pkgs.docker
  ];

  # Docker
  virtualisation.docker.enable = true;
  users.users.nixos.extraGroups = [ "docker" ];

  # Set up nix-ld
  programs.nix-ld.enable = true;

  # Windows Subsystem for Linux
  wsl.interop.includePath = false;
  wsl.interop.register = true;
  wsl.extraBin = [
    {
      name = "code";
      src = "/mnt/c/Users/User/scoop/apps/vscode/current/bin/code";
    }
  ];
```
