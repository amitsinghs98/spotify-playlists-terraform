# Creating Multiple Spotify Playlists Using Terraform

This repository demonstrates how to use **Terraform** to automate the creation of multiple playlists on **Spotify**.

## Overview

Spotify offers a vast range of functionalities through its Web API. With **Terraform**, a powerful Infrastructure as Code (IaC) tool, we can automate the process of creating multiple playlists on Spotify. This project utilizes the **Spotify API** and **Terraform** to create playlists efficiently with minimal manual effort.

## Prerequisites

Before you get started, you will need the following:

- **Spotify Developer Account**: You need a Spotify Developer account to obtain the necessary credentials to interact with the Spotify API.
  - Sign up at: https://developer.spotify.com/dashboard/applications
- **Spotify API Credentials**: Obtain your **Client ID** and **Client Secret** from the Spotify Developer Dashboard.
- **Terraform**: Install Terraform on your local machine. Follow the official instructions here: https://learn.hashicorp.com/tutorials/terraform/install-cli
- **curl** (for testing the Spotify API directly from the command line).

## Steps to Set Up

### 1. Clone the Repository
Clone this repository to your local machine:
```bash
git clone https://github.com/amitsinghs/spotify-playlists-terraform.git
cd spotify-playlists-terraform
```

### 2. Configure the Spotify API Credentials
In order to authenticate Terraform with Spotify's API, you need to set up your Spotify API credentials:
- Set the environment variables for the **Spotify Client ID** and **Client Secret**.

```bash
export SPOTIFY_CLIENT_ID="your-client-id"
export SPOTIFY_CLIENT_SECRET="your-client-secret"
```

Alternatively, you can configure these in the `terraform.tfvars` file.

### 3. Initialize Terraform
Run the following command to initialize Terraform and download the necessary provider plugins:
```bash
terraform init
```

### 4. Modify the Playlist Data
Edit the `playlists.tf` file to include the details for the playlists you want to create. You can define multiple playlists with their respective names, descriptions, and track URLs.

```hcl
resource "spotify_playlist" "my_playlist" {
  name        = "My Playlist"
  description = "This is my awesome playlist created via Terraform!"
  tracks      = ["track_uri1", "track_uri2", "track_uri3"]
}
```

### 5. Apply the Terraform Configuration
Run the following command to apply the Terraform configuration and create the playlists on Spotify:
```bash
terraform apply
```

Terraform will prompt you to confirm the changes. Type `yes` to proceed.

### 6. Verify the Playlists
After running `terraform apply`, go to your Spotify account, and you should see the playlists created automatically.

### 7. Clean Up
To delete the created playlists, you can run:
```bash
terraform destroy
```

This will remove the playlists from your Spotify account.

## File Structure

```bash
.
├── main.tf                # Main Terraform configuration file
├── playlists.tf           # Spotify playlist configurations
├── terraform.tfvars       # Optional file to store sensitive variables
└── README.md              # This README file
```

## Contributing

If you'd like to contribute to this project, feel free to fork the repository, make changes, and submit a pull request. Contributions are always welcome!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
