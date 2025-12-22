#!/usr/bin/env python3

import subprocess
import os

def main():
    # Check if the current working directory is the repository root
    if not os.path.exists('.git'):
        print("Error: This script must be run from the repository root.")
        return 1

    # Update the package index
    subprocess.run(['pip', 'install', '--upgrade', 'pip'])

    # Install dependencies
    subprocess.run(['pip', 'install', '-r', 'requirements.txt'])

    # Run the linter and formatter
    subprocess.run(['flake8', '.'])
    subprocess.run(['black', '--check', '.'])

if __name__ == '__main__':
    main()