<div align="center">

# YAMW Subsonic Pipeline

<img src="https://raw.githubusercontent.com/Arjuna-Ragil/YAMW/main/documentation/YAMW%20logo.png" alt="YAMW Logo" width="150">
<br><br>

[![YAMW Client](https://img.shields.io/badge/Main_Client-YAMW-blue?logo=github)](https://github.com/Arjuna-Ragil/YAMW)
[![Release](https://img.shields.io/github/v/release/Arjuna-Ragil/YAMW)](https://github.com/Arjuna-Ragil/YAMW/releases)
[![Wails Build](https://github.com/Arjuna-Ragil/YAMW/actions/workflows/release.yml/badge.svg)](https://github.com/Arjuna-Ragil/YAMW/actions)

> *A self-hosted backend stack for automated media downloading and Subsonic streaming. For integrating with YAMW*

</div>

##

This repository contains the infrastructure configuration to deploy a personal media server. It acts as the backend companion for [YAMW](https://github.com/Arjuna-Ragil/YAMW), providing seamless media ingestion and instant streaming capabilities.

The pipeline utilizes **Docker Compose** to orchestrate two main services:
*   **[MeTube](https://github.com/alexta69/metube):** A web GUI for `yt-dlp`, configured to automatically download media, embed metadata, and save it to a shared volume.
*   **[Navidrome](https://github.com/navidrome/navidrome):** A modern Music Server and Streamer compatible with the Subsonic API, which instantly indexes the downloaded files.

## Installment

1. Clone this repository to your server:
   ```bash
   git clone https://github.com/Arjuna-Ragil/YAMW-Subsonic-Pipeline.git
   cd YAMW-Subsonic-Pipeline
   ```
   
2. Start the media pipeline:
   ```bash
   docker compose up  -d
   ```
   
3. Access the services via your server's IP address:
   * http://<SERVER_IP>:8082
   * http://<SERVER_IP>:4533
  
4. Add your media:
   * Make sure that navidrome is using the correct file path. Adjustment maybe needed depending on your file path.
   * Search your favorite song in youtube or youtube music.
   * Copy and paste the link to metube. After download is completed, check Navidrome or relaunch YAMW to see the updated music list.

## Architecture
The services are connected via a shared local volume (./music). When a media file is downloaded via MeTube, it is directly piped into the shared directory, allowing Navidrome to detect, index, and serve the new media to the YAMW client immediately.

Disclaimer: This project is for educational purposes and personal archiving of royalty-free, creative-commons, or personally owned media. The developer is not responsible for any misuse of this tool that violates third-party Terms of Service. Thanks!
