# 🏗️ Customizable NixOS Install Media Builder

This repository provides the necessary configurations and GitHub Actions workflows to build customizable NixOS installation media for various hardware platforms. Currently it supports creating installation media for Intel Macbook Pro (x86_64) and Raspberry Pi 4 (aarch64) by providing your own `configuration.nix` file.

## Repository Structure

- `builders/`: This directory contains pre-configured templates for building NixOS installation media. It currently includes the following folders:
    - `macbook-pro-x86_64`: Base configuration to produce an ISO for booting an Intel Macbook Pro.
    - `rpi4-aarch64`: Configuration to create an SD card image for booting a headless server on a Raspberry Pi 4.

- `.github/workflows/`: This directory contains GitHub Actions workflows for building installation media for different hardware platforms. It includes:
    - `build-nix-iso-docker.yml`: Workflow to build an ISO image for x86_64 (Intel) platforms.
    - `build-nix-sdcard-docker.yml`: Workflow to create an SD card image for aarch64 (Raspberry Pi 4) platforms.

## How to Use

### 1. Use this Repository as a Template

Start by using this repository as a template to create your own customized repository for your contributions. Click the "Use this template" button at the top of the repository page to create a new repository based on this template in your GitHub account. This allows you to make changes and use the provided GitHub Actions workflows in your own repository.

### 2. Create a Builder

Inside your forked repository, navigate to the `builders/` directory. Create a subdirectory for your hardware platform (e.g., `macbook-pro-x86_64`, `rpi4-aarch64`). In this subdirectory, create a `default.nix` file that specifies your desired NixOS configuration. You can customize packages, services, and other settings according to your needs.

### 3. Add Secrets to Your GitHub Repository

To securely pass secrets and keys to the GitHub Actions workflows, it's important to consider the security of your secrets. NixOS configurations are stored in the NixStore, and any secrets included in these configurations can potentially be committed in plaintext. Storing secrets in plaintext in your NixStore is not a secure practice and can pose a security risk.

To enhance security and ensure that sensitive information is not leaked, you should use a secrets management solution. By using `age` or another secrets management solution, you can mitigate the risk of exposing sensitive information in your NixOS configurations.


### 4. Configure GitHub Actions Workflow

Edit the appropriate GitHub Actions workflow file (`build-nix-iso-docker.ymll` or `build-nix-sdcard-docker.yml`) in the `.github/workflows/` directory to specify the target hardware platform and any additional parameters required for your configuration.

### 5. Push Changes and Trigger the Workflow

Once you've added your Builders configuration and configured the GitHub Actions workflow, commit and push your changes to your forked repository. This will trigger the workflow, and you can monitor its progress in the "Actions" tab of your repository.

### 6. Download the Install Media

After the workflow successfully completes, you can download the generated NixOS installation media from the "Artifacts" section in the workflow run. The artifacts will be labeled with your hardware platform.

## Supported Hardware Platforms

- Intel Macbook Pro (x86_64)
- Raspberry Pi 4 (aarch64)

## Contributing

If you'd like to add support for additional hardware platforms or improve the existing workflows, please feel free to contribute to this repository by creating a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
