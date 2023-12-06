# Mediamonks



# Set the entrypoint script content directly
ENTRYPOINT [ \
    "#!/bin/bash", \
    "", \
    "# entrypoint.sh", \
    "", \
    "# Execute the configuration script with environment variables", \
    "./config.sh --unattended --name \"$RUNNER_NAME_PREFIX\" --url \"$REPOSITORY_URL\" --pat \"$GITHUB_PAT\"", \
    "", \
    "# Execute the run script", \
    "./run.sh" \
]


# Make the entrypoint script executable
RUN chmod +x entrypoint.sh


docker run -e RUNNER_NAME_PREFIX=my-custom-runner \
           -e REPOSITORY_URL=https://github.com/your-username/your-repo \
           -e GITHUB_PAT=your-github-pat \
           my-github-runner:latest


# Set the entrypoint script
ENTRYPOINT ["./entrypoint.sh"]
