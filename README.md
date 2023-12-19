# VRust
Automated Vulnerability Detector for Solana Smart Contracts

## Full Installation
### Build
To build docker image and then run it, execute these commands:
```
docker build -t vrust .
docker run -it vrust:latest
```

### Analyzing Solana Smart Contracts
VRust will automatically detect vulnerabilities and generate a PDF report as a result. To run VRust, use the following command:
```
python3.9 examples/run.py -v target/debug/vrust -o SmartV_Report_Generator/
```

Here is a list of arguments:
+ `-o`: Location to .pdf converter project directory (path to `SmartV_Report_Generator`).
+ `-v`: Location to vrust build (path to `target/debug/vrust`).
+ `-c`: destList of specific programs to run only (use this when you want to run Vrust on a subset of existing programs).
+ `-r`: Location to store reports.
+ `-s`: Location to current working directory of programs.

To only receive a JSON report without converting it to a PDF, you can comment out the `convert_json_to_pdf(programData)` line in `run.py`.

Do not forget that Vrust is an old tool and is unable to analyze projects using Rust versions newer than nightly-2022-02-24. To analyze newer projects, either use another tool, or downgrade the project. I've already upgraded Vrust to support newer versions, but Rust has fundamental changes after nightly-2022-02-24. Upgrading it requires solid knowledge of Rust and a deep understanding of Vrust's implementation.

Do not run Vrust on your system without using Docker, as its dependencies must have older versions to meet its requirements.

## Research Paper

For more information, please refer to our [VRust Paper](https://dl.acm.org/doi/abs/10.1145/3548606.3560552) accepted [CCS'2022](https://www.sigsac.org/ccs/CCS2022/).


