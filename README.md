# vinca
 Conda recipe generator for ROS packages
 
**WARNING**:
This project is at a super early stage.
No guarantees everything works.

## Concept

The tool generates `conda` recipe to capture all the selected ROS packages.
Later, one can use `conda-smithy` to auto-generate pipeline to release `conda` binary packages.

## Example

First you have to create a `vinca.yaml` to describe ROS information for `vinca` to do the magic generating the recipe.

```yaml
# vinca.yaml
ros_distro: eloquent

# optionally, a fat archive can be generated too.
fat_archive: true
name: ros-eloquent-fat-ament-cmake

# mapping of rosdep keys
# it can be also used to shadow the unwanted packages.
conda_index:
  - 'https://raw.githubusercontent.com/ros-forge/rosdep-conda-forge/master/rosdep/conda-forge.yaml'

# packages to skip
packages_skip_by_deps:

# packages to include
packages_select_by_deps:
  - ament_cmake

# patch directory
patch_dir: ./patch
```
