git clone https://github.com/BespokeSynth/BespokeSynth.git
cd BespokeSynth/
git checkout v1.1.0
# from azure-pipelines.yml - alsa from there did not exist in for debian bullseye
apt-get install -y devscripts libxcb-cursor-dev libxcb-keysyms1-dev libxcb-util-dev libxkbcommon-dev libxkbcommon-x11-dev ninja-build xcb libgtk-3-dev libwebkit2gtk-4.0 libwebkit2gtk-4.0-dev libcurl4-openssl-dev alsa-tools libasound2-dev libjack-dev libfreetype6-dev libxinerama-dev libxcb-xinerama0 libxinerama1 x11proto-xinerama-dev libxrandr-dev libgl1-mesa-dev libxcursor-dev libxcursor1 libxcb-cursor-dev libxcb-cursor0 libusb-1.0.0-dev patchelf python3-dev
git submodule update --init --recursive
cmake -Bignore/build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/opt/bespokesynth
cmake --build ignore/build --parallel 4 --config Release
cmake --install ignore/build
