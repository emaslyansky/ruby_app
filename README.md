# ruby_app
Test ansible for ruby_app

We use 3 roles: nginx from galaxy and app and postgres hand-made.

# HOW TO DEPLOY

## define your variables in ./defaults
app_name: "rubyApp"

service_user: "nginx"

service_group: "nginx"

rails_env: "production"

rails_log_to_stdout: 1

db_host: "127.0.0.1"

db_port: 5432

db_name: "{{ app_name }}_prod"

db_user: "{{ app_name }}_dbuser"

db_password: "postgres"

git_user: "" # your git user

git_password: "" # your git passwd

## specify your ssh_key for target host in ansible.cfg
private_key_file=######

## edit hosts.ini (don't forget)

## define your git with app ruby
/ruby_app_slurm/roles/app/tasks/main.yml
"https://{{ git_user | urlencode }}:{{ git_password | urlencode }}@gitlab.########.git"

## changed files
/ruby_app_slurm/roles/app/templates/startup.j2

/ruby_app_slurm/roles/app/templates/service.j2

/ruby_app_slurm/roles/app/files/nginx.conf
