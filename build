#!/bin/bash

echo "capture version info"
VERSION=`git rev-parse --short HEAD`

echo "clone the imgmt repo"
git clone git@github.com:josephharding/imgmt.git

echo "cd into imgmt"
cd imgmt

echo "run the packaging play against inventory: ${1}"
ansible-playbook -i $1 package-docker-app.yml \
  --extra-vars "@../build_params.json" \
  --extra-vars "project_root='`pwd`/../' image_version='${VERSION}'"

echo "leave the imgmt dir"
cd ..

echo "clean up the deploy dir"
rm -rf imgmt
