---
title: Polecenie delete interfejsu wiersza polecenia NuGet | Dokumentacja firmy Microsoft
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: c213a07a-711d-47e0-9ee6-1d582e6cdb69
description: Dokumentacja dla polecenia delete nuget.exe
keywords: "nuget usunąć odwołanie, usuń pakiet polecenia"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 92af9dc356f3932347864976496e0ba1216496c9
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="delete-command-nuget-cli"></a>Usuwanie polecenia (NuGet CLI)

**Dotyczy:** publikowania pakietu &bullet; **obsługiwane wersje:** wszystkie

Usuwa lub unlists pakietu ze źródła pakietu. Dla nuget.org, polecenia delete [unlists pakietu](../policies/Deleting-Packages.md).

## <a name="usage"></a>Użycie

```
nuget delete <packageID> <packageVersion> [options]
```

gdzie `<packageID>` i `<packageVersion>` identyfikować dokładną pakiet do usunięcia lub unlist. Dokładne zachowanie zależy od źródła. Foldery lokalne na przykład pakiet został usunięty; w przypadku nuget.org pakietu jest nieznajdujące się na liście.

## <a name="options"></a>Opcje

| Opcja | Opis |
| --- | --- |
| apiKey | Klucz interfejsu API dla repozytorium docelowej. Jeśli nie występuje, określony w *%AppData%\NuGet\NuGet.Config* jest używany. |
| ConfigFile | *(2.5 +)*  Pliku konfiguracji NuGet w celu zastosowania. Jeśli nie zostanie określony, *%AppData%\NuGet\NuGet.Config* jest używany. |
| ForceEnglishOutput | *(3.5 +)*  Wymusza nuget.exe przy użyciu opartego na język angielski, niezmienna kultura. |
| Pomoc | Wyświetla Pomoc dla polecenia. |
| Nieinterakcyjne | Pomija wyświetla monit o dane wejściowe użytkownika lub potwierdzeń. |
| Źródło | Określa adres URL serwera. Adres URL nuget.org jest `https://api.nuget.org/v3/index.json`. Dla prywatnych źródeł danych, zastąp nazwę hosta, na przykład *%hostname%/api/v3*. |
| Szczegółowość | Określa ilość szczegółów wyświetlanych w danych wyjściowych: *normalne*, *quiet*, *szczegółowe (2.5 +)*. |

Zobacz też [zmienne środowiskowe](cli-ref-environment-variables.md)

## <a name="examples"></a>Przykłady

```
nuget delete MyPackage 1.0

nuget delete MyPackage 1.0 -Source http://package.contoso.com/source -apikey A1B2C3
```