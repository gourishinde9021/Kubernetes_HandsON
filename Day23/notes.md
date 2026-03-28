To check who are you,
```
kubectl auth whoami
```
To check who you are,
```
k auth can-i create pod
```
To get the crt file in decoded format
```
kubectl get csr krishna -o jsonpath='{.status.certificate}'| base64 -d > krishna.crt
```


