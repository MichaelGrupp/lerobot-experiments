This repo contains a minimal Pixi workspace for experimenting with the `lerobot` repo and the `SO-ARM101` robot model.
`lerobot` is used from a [forked](https://github.com/MichaelGrupp/lerobot), editable source with some modifications for the [Rerun](https://rerun.io/) visualization like:
* URDF support
* transform support

Assuming that you have [installed Pixi](https://pixi.prefix.dev/latest/installation/) already, initialize the submodule repos and the Pixi workspace:
```
git submodule init && git submodule update

pixi shell
```
This should™ resolve all the dependencies and install everything that is needed.

Find the ports of follower and leader using `lerobot-find-port` and the camera index via `lerobot-find-camera`, then run e.g. teleop mode:
```
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5A7C1164541 \
    --robot.id=my_awesome_follower_arm \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5A7C1172981 \
    --teleop.id=my_awesome_leader_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 30}}" \
    --display_data=true
```
If calibration is needed, follow the instructions shown in the terminal (see also [here](https://huggingface.co/docs/lerobot/so101#calibration-video)).

**NOTE**: if you've used another version of `lerobot` before (e.g. via pip), the stored calibration can be incompatible and lead to a buggy process. Force a recalibration by deleting previous calibrations: `rm -r ~/.cache/huggingface/lerobot/calibration`.

See the [LeRobot docs](https://huggingface.co/docs/lerobot/il_robots) for more tutorials.

https://github.com/user-attachments/assets/e897cf47-d26a-49b2-a95e-3d73d2070ef5



