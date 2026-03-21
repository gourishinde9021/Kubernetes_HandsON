1. Create ssl key
```   
openssl genrsa -out adam.key 2048
```
2. Create CSR - self signing
```
openssl req -new -key adam.key -out adam.csr -subj "/CN=adam"

cat adam.csr | base64 | tr -d "\n"
```
3. Copy oneline key in certi.yaml
```
kubectl apply -f certi.yaml
```
4. CSR is created
```
kubectl get CertificateSigningRequest
kubectl describe csr
```
5. Approve CSR as Kubenetes admin
```
kubectl certificate approve adam
```
6. Get the CSR token to give to user to use in the service
```
kubectl get csr adam -o yaml > issuedcert.yaml

echo "CSR-TOKEN" | base64 -d
```
