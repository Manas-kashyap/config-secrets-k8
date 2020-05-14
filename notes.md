# Ways to create base64 codes
echo -n 'admin' | base64
echo -n 'password' | base64
# To create Secret using command line
kubectl create secret generic secret-demo --from-literal=username=manas --from-literal=password=kashyap
# To create Secret using command line (when we have everything stored in file)
kubectl create secret generic secret-demo --from-file=./secrets

"We can use secrets in 2 ways as env variables in pod or using volumes "

* Note , if you change the secret file and if you have mounted it as volume the secrets will change but if you have mounted it as env the existing containers data wont change and  the new nes will get the updated secrets

# To create ConfigMap using adhoc command

kubectl create configmap configmap-demo --from-literal=firstname=manas --from-literal=lastname=kashyap

also if you want to use a file inside the yaml , you can use name of the file under data section and then | (pip sysmbol) followed by the variables and values

```  volumes:
  - name: config
    configMap:
      name: demo-config
      items:
        - key: manas.cnf
          path: mannas.cnf  ```


"Decoding base64"
echo 'MWYyZDFlMmU2N2Rm' | base64 --decode