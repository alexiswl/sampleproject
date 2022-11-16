# Copyright 2020 Pants project contributors.
# Licensed under the Apache License, Version 2.0 (see LICENSE).

# This target sets the metadata for all the Python non-test files in this directory.
resource(
  name="sampleproject_res",
  # IDEAL
  source="pyproject.toml"
)

# Create pex binary
pex_binary(
    name="pex_binary",
    entry_point="sample.simple",
    dependencies=[":sampleproject_res"]
)

# Required for pyox binary
python_distribution(
    name="sample_dist",
    # IDEAL
    # dependencies=[
    # ":sampleproject_res"
    #],
    # FIX - otherwise sample project is not collected
    dependencies=[
     ":sampleproject_res",
     "src/sample:lib"
    ],
    provides=python_artifact(
            name="sampleproject",
            version="2.0.0"
    )
)

# Build pyoxidizer binary
# Build pyoxidizer binary
pyoxidizer_binary(
    name="pyox_binary",
    entry_point="sample.simple",
    dependencies=[":sample_dist"]
)
