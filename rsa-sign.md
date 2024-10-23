## RAS SHA256 sign 


1. Input a name of target user. (e.g., charles). 
2. In Recipe, add RSA sign and enter the private key. Then add Base 64. [Cyberchef Recipe](https://cyberchef.io/#recipe=RSA_Sign('-----BEGIN%20RSA%20PRIVATE%20KEY-----%5CnMIICXQIBAAKBgQDku/9mnwqcgB5IMQtKLoiGJqD2THVhFK2MBqiHjZ8wVum50vXy%5Cne9yFmwBNCgdpMEFGxc%2B4Ajsv9ueQvhiR7e0qYO1cUdMoGMFkCvuYvGoSlbLIgQnF%5Cnq8FbZv7oteW8ITmYhkqikJ9qqC9jVErIGhB8cTlx5wpRm7V0AP/C1QksxQIDAQAB%5CnAoGANrRnvulmpktV8roYEyPR7xOqB339zLwfTZACGnlaizseJx03SUkqUqHhjotJ%5CnfnTWB9EjfsS51xzcARgV1EDtKXO9%2BQPlJsmYj1mL9fVdMd%2BGoNIjZVR2%2BhJ7D%2BfY%5CnSJy6Qddhfrz5rpCQ8YV1uWFIQwFjag0GerL/PUFjM3CRe7kCQQD4zvJJjjhdlkpX%5CnXbFJY5LoOoN5azW5m/vQSoqpLdjst9Clam1FJ%2BdJ6%2B/Q3Lzp2AucKUmCcYWkutwb%5Cn4mNqE6G/AkEA61iDi9frmmH%2B6gQnx2G2pFkRgO%2BMhK2%2BS4XHrN/c2fn7Ej6LXGF4%5CnrroO9lOzmHZN%2B9zqKGsRx5UIMF5ldvcKewJBAM816mp/20l1xOwFx4RLPSnSsXQJ%5CnaXDvC0RpEBndaO%2BcFlPs0pvpo6HYsJzNeTd3ChQ//kx4psiOJonCfPD28JkCQDjA%5Cns5g5jXtBPnO4ZM9T5PNk9y%2BclMo6C7WyoSAzK9L00XLo2jqA1tVr0MfeD2Uowk2G%5CnTIFKsJLsgXkIindRw5kCQQCclbh/dpchNHO%2BuZaD2OijzwZHBM5BgJ0fy4O7IMw/%5CnaNMiboJ3a09LUqvOIp3r5QQuohcQog/IzxF1Leu2VHxu%5Cn-----END%20RSA%20PRIVATE%20KEY-----%5Cn','','SHA-256')To_Base64('A-Za-z0-9%2B/%3D')&input=Y2hhcmxlcw)
3. Copy the output, then replace the signature with it. 

```
{"username":"charles","signature":cmVwbGFjZSB0aGUgb3V0cHV0IChCYXNlIDY0KSBmcm9tIHRoZSBwcmV2aW91cyBzdGVwIA=="}
```

4. Open another cyberchef, convert the token above to base 64. Note: Replace `=` with `%3D` [Cyberchef recipe](https://cyberchef.io/#recipe=To_Base64('A-Za-z0-9%2B/%3D')&input=eyJ1c2VybmFtZSI6ImNoYXJsZXMiLCJzaWduYXR1cmUiOiJwUkZCazNJalp0clY3MDN4Skg3d2J0RUpLME4vK0UyOWlucHVGUndjcVFsWGpGZVBIUTBMQ3NNS1Nkd2RjQjYrbjFQc3UzNTdaeC9CTGhlbXNqR2h6aVE2OGpiNVgyN29PaUZZR0lDU1ZyM1VzNXZkdUw0Ym9MVms5ZWRBaTFCdE82VUZvbW9XY0xMODlqcjFjbFMyWkVEMjFIVWRUZkl1cGUrcWdGL0g4Vzg9In0)
5. On the website, login using an authorized user, then replace session in the Storage section in the dev tool. 

