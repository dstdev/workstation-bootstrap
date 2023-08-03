# Usage

    ansible-pull -U https://github.com/dstdev/workstation-bootstrap -K

    #
    ansible-pull -U https://github.com/dstdev/workstation-bootstrap -K -e 'git_email=andrew.a.kail@gmail.com' -e 'git_name="Andrew Kail"'

# Adding reuseable variables

If you want to shorten the execution of the above and get your git and vim settings initialized, you can create
a yaml file with those variables and call it directly

    # Set in vars.yaml
    git_email: andrew.a.kail@gmail.com
    git_name: "Andrew Kail"
    enable_vim: true

Then reference the file when executing ansible-pull.

    ansible-pull -U https://github.com/dstdev/workstation-bootstrap -K -e "@vars.yaml"