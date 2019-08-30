---
layout: post
title: Générer des QR Code en PowerShell
subtitle: Utilisation de Zen.Barcode
bigimg: /img/qrcode.jpg
tags: [powershell,qrcode,informatique]
---
Pour un projet professionnel, j'ai eu besoin de générer automatiquement des QR Code à partir d'entrées dans une base de données. J'ai d'abord commencé le projet en C# grâce à la librairie Zen.Barcode, mais vu qu'il fallait apporter des modifications régulièrement au code, il était plus simple de passer dans un langage non compilé et plus facile à déployer. J'ai vite fait chercher des exemples pour utiliser la librairie en PowerShell, et comme il n'y a pas beaucoup d'exemples, j'ai décidé de mettre ce petit bout de code à disposition, si jamais ça peut vous éviter de chercher pour rien ! 

Le code suivant, génère donc une image contenant la chaîne de caractères "Mes données !"
Il est également possible de générer l'image dans un autre format, et à d'autres dimensions. 

Pour télécharger la dll directement, vous pouvez [suivre ce lien](https://github.com/brouwerthomas/brouwerthomas.github.io/raw/master/img/Zen.Barcode.Core.dll "Télécharger Zen.Barcode.Core"), ou alors passer par le package NuGet et en extraire la dll qui nous intéresse ici.

```powershell
Add-Type -Path "D:\QR\Zen.Barcode.Core.dll" 
$qr = [Zen.Barcode.CodeQrBarcodeDraw]::new()
$outFile = "D:\QR\QR.jpg"
$data = "Mes données !"
$qr.Draw($data, 70).Save($outFile, [System.Drawing.Imaging.ImageFormat]::Jpeg)
```
