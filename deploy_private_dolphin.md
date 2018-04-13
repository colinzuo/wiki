# clone infra repo first

# build image tar, xxx.tar
```
cd infra/docker/dolphin
cp PRIVATE_DOLPHIN bin/
./build_private.sh 1234
```

# stop old dolphin, execute on docker master node (node1, node2, node3)
```
docker stack rm haishen_dolphin
```

# update dolphin image on swarm nodes (node1, node2, node3)
```
rm xxx.tar;scp xxx.tar .;docker load -i xxx.tar
```

# depoly new dolphin
```
cd infra/ansible/deploy/setup_dolphin/
cp haishen_dolphin_inventory temp_dolphin_inventory
# modify temp_dolphin_inventory according to real environment
./deploy_dolphin.sh ./temp_dolphin_inventory "1234"
```
