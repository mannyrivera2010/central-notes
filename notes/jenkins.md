### Setting up Jenkins for python project (ozp-backend)
Setting up new job config


Project name: build-backend-latest
Github Project: https://github.com/aml-development/ozp-backend/
Throttle Concurrent Builds: 
- Maximum Total Concurrent Builds = 1
- Maximum Concurrent Builds Per Node = 1
Restrict where this project can be run: ci-jenkins.amlng.di2e.net
Source Code Management: 
- Repositories: https://github.com/aml-development/ozp-backend.git
- Credentials: - none -
Branches to build: */master
Git executable: Default
Build Triggers: 
- Build when a change is pushed to GitHub
Build Environment:
- Delete workspace before build starts
- Abort the build if it's stuck
-- Time-out strategy: Absolute , Timeout minutes: 15
Build: 
Execute Shell:
````bash
# create clean python env
rm -rf ~/python_envs/ci-env/
mkdir ~/python_envs/ci-env/
pyvenv-3.4 ~/python_envs/ci-env/
source ~/python_envs/ci-env/bin/activate
# install prereqs (clean)
pip install --upgrade pip
# this is super sketchy, but without it, psycopg2 will fail to install (won't be
# able to find lib2to3 stuff)
# /opt/lib2to3 was copied from a clean Python-3.4.3 build (Lib directory)
cp -r /opt/lib2to3 ~/python_envs/ci-env/lib/python3.4/site-packages/
export PATH=/usr/local/pgsql/bin:$PATH
pip install -r requirements.txt --no-cache-dir -I
# make the release
python release.py --no-version
````

Post-build Actions: 
Archive the artifacts: backend*.tar.gz

Send Build artifacts over SSH:
ci-latest.domain.net
Transers:
Exec command: ````sudo /home/jenkins/ozp_deploy.sh ${JOB_NAME} ${BUILD_NUMBER}````

Delete Workspace when build is done.



