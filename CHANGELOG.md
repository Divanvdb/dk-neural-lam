# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [unreleased](https://github.com/mllam/neural-lam/tree/main)

### Fixed

- `all_gather_cat` function in `ar_model.py` removed since it messes with the shapes of the my losses
- Added an `use_numpy` variable to the `create_dataarray_from_tensor` functions for both `weather_dataset.py`, `train_model.py` and `ar_model.py` to be able to use this funtion in Notebooks to generate data_arrays


## [v0.1.0](https://github.com/Divanvdb/dk-neural-lam)

- Initialised the ERA5 2020 testing data and config files `test_config.yaml` and `test.datastore.yaml`
- Added images to the `README.md` file
- Created a new `validate_model.py` file for the evaluation phase
- Updated the Lightning Trainer in `train_model.py` to include multi-GPU training and a profiler

## [v0.1.1](https://github.com/Divanvdb/dk-neural-lam)

- Remade the test datastore with `label = train` in the `test.datastore.yaml` file
- Added a train option into the `setup` function of `weather_dataset` to create a testing datastore with unshuffled dataloader
- Redid `validate_model.py` to produce and `output_1431x7x49x69` file for weather evaluation using untrained model

## [v0.1.2](https://github.com/Divanvdb/dk-neural-lam)

- Ensured the **standardization** of the weather data is done correctly
- Reduced `n_boundary_points=2` to `n_boundary_points=0` in `mdp.py` to ensure the model doesn't use future forcings with `--num_future_forcing_steps 0` 
- Used: `saved_models\train-graph_lam-4x64-01_23_13-3100\min_val_loss.ckpt`
- Added a `total` variable to the `validate_model.py` script

## [v0.1.3](https://github.com/Divanvdb/dk-neural-lam)

- Updated the `train_model.py` to have the default values in the `args`

## [v0.1.4](https://github.com/Divanvdb/dk-neural-lam)

- Found that the **standardization** happening within the `_build_item_dataarrays()` function constrains the **CPU**

- `.yaml` setting files also updated to only include `wind_speed850.0hPa` at this stage, but might revert
- Brought back the `boundary_points = 5` to see what this would affect
- Added a `plot_data.ipynb` notebook that visualizes the output from `validate_model.py`

## [v0.1.5](https://github.com/Divanvdb/dk-neural-lam)

- Fixed the transposed grid problem in `plot_graph.py`
- Moved the **standardization** to **GPU** before computing in the `_build_item_dataarrays()` of `weather_dataset.py`

## [v0.1.6](https://github.com/Divanvdb/dk-neural-lam)

- Added new `test_step` function to the `ar_model.py` script to generate testing data for visualization
- Set the defaults in the `train_model.py` script
- Brought back all the variables for training

## [v0.1.7](https://github.com/Divanvdb/dk-neural-lam)

- Added **3h** timestep dataset
- Added larger dataset with square setup

## [v0.1.8](https://github.com/Divanvdb/dk-neural-lam)

- Altered the dataset to include only `100x100` points
- `base_graph_model.py` now outputs the **structures** of the *embedding models*

## [v0.1.9](https://github.com/Divanvdb/dk-neural-lam)

- Added a medium-sized `80 x 80` set to ensure the model learns patterns over the region of SA
- Created new `base_model.py` for testing purposes