# RMK

* build the image `podman build -t rmk -f .devcontainer/Dockerfile .`.
* start a container `podman run -it --rm --volume $PWD:/workspace:Z --workdir /workspace rmk`.
* run `cd rmk; rustup target add thumbv7em-none-eabihf; cd ..`.
* run `npm run buildrmkclean`.
* Press the reset button twice on the MCU.
* The MCU should be mounted a drive named `XIAO-SENSE`.
* copy `rmk/sessile.uf2` to `XIAO-SENSE`.
* the MCU will detect the new firmware and automatically reboot.
