# Display help text

	podman run --rm docker.io/alexjc/neural-enhance --help

# Artifically enhance image

	podman run --rm -v $(pwd):/ne/input:z -it alexjc/neural-enhance --zoom=1 --model=repair /ne/input/IMAGE_PATH
