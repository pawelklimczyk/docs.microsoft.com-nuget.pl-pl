---
title: Interfejs wiersza polecenia NuGet polecenia update
description: Dokumentacja dotycząca polecenia update nuget.exe
author: karann-msft
ms.author: karann
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: fc34550b3669d83466318645987cfd3078bc3c18
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43545103"
---
# <a name="update-command-nuget-cli"></a>update command, polecenie (interfejs wiersza polecenia NuGet)

**Dotyczy:** pakietu zużycie &bullet; **obsługiwane wersje:** wszystkie

Aktualizuje wszystkie pakiety w projekcie (przy użyciu `packages.config`) do jego najnowszej dostępnej wersji. Zaleca się uruchomienie ["restore"](cli-ref-restore.md) przed uruchomieniem `update`. (Aby zaktualizować poszczególnych pakietów, użyj [ `nuget install` ](cli-ref-install.md) bez określania numeru wersji, w którym wielkość NuGet instaluje najnowszą wersję.)

Uwaga: `update` nie działa z interfejsem wiersza polecenia, uruchomione w Mono (Mac OS x lub Linux) lub przy użyciu formatu PackageReference.

`update` Polecenie aktualizuje również odwołania do zestawu w pliku projektu, pod warunkiem tych odwołuje się już istnieje. Jeśli dodano zestaw zaktualizowany pakiet, nowe odwołanie jest *nie* dodane. Nowe zależności pakietu nie ma również ich dodać odwołania do zestawu. Aby uwzględnić te operacje w ramach aktualizacji, należy zaktualizować pakiet w programie Visual Studio za pomocą interfejsu użytkownika Menedżera pakietów lub konsoli Menedżera pakietów.

To polecenie można również zaktualizować nuget.exe się przy użyciu *-self* flagi.

## <a name="usage"></a>Użycie

```cli
nuget update <configPath> [options]
```

gdzie `<configPath>` identyfikuje albo `packages.config` lub plik rozwiązania, który zawiera listę zależności projektu.

## <a name="options"></a>Opcje

| Opcja | Opis |
| --- | --- |
| ConfigFile | Plik konfiguracyjny NuGet do zastosowania. Jeśli nie zostanie określony, `%AppData%\NuGet\NuGet.Config` (Windows) lub `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) jest używany.|
| FileConflictAction | Określa akcję wykonywaną po wyświetleniu monitu o zastąpienie lub zignorować istniejące pliki przywoływanego przez projekt. Wartości są *zastąpić, Ignoruj Brak*. |
| ForceEnglishOutput | *(3.5 +)* Wymusza nuget.exe przy użyciu opartego na język angielski, niezmienna kultura. |
| Pomoc | Wyświetla Pomoc dla polecenia. |
| Id | Określa listę identyfikatorów, aby zaktualizować pakiet. |
| MSBuildPath | *(4.0 +)*  Określa ścieżkę program MSBuild będzie używać za pomocą polecenia pierwszeństwo `-MSBuildVersion`. |
| MSBuildVersion | *(3.2 +)*  Określa numer wersji MSBuild ma być używany za pomocą tego polecenia. Obsługiwane wartości to 4, 12, 14, 15. Domyślnie program MSBuild w ścieżce jest pobierana w przeciwnym razie domyślnie najwyższy zainstalowanej wersji programu MSBuild. |
| Nieinterakcyjnym | Wyłącza monity dotyczące danych wejściowych użytkownika lub potwierdzenia. |
| Wersja wstępna | Zezwala na aktualizację do wersji wstępnych. Ta flaga nie jest wymagana podczas aktualizowania pakietów wydań wstępnych, które są już zainstalowane. |
| RepositoryPath | Określa folder lokalny, w którym są zainstalowane pakiety. |
| Bezpieczne | Określa, która aktualizuje tylko z najwyższą wersją dostępne w ramach tej samej wersji głównych i pomocniczych zgodnie z zainstalowanym pakietem zostanie zainstalowana. |
| Samodzielna | Nuget.exe aktualizacji do najnowszej wersji; wszystkie inne argumenty są ignorowane. |
| Źródło | Określa listę źródeł pakietów (jako adresy URL) na potrzeby aktualizacji. Jeśli argument jest pominięty, polecenie używa źródeł dostarczane w plikach konfiguracyjnych, zobacz [zachowania programu NuGet Konfigurowanie](../consume-packages/configuring-nuget-behavior.md). |
| Szczegółowość | Określa ilość szczegółów wyświetlanych w danych wyjściowych: *normalne*, *cichy*, *szczegółowe*. |
| Wersja | W przypadku użycia z jednym Identyfikatorem pakietu, określa wersję pakiet do zaktualizowania. |

Zobacz też [zmiennych środowiskowych](cli-ref-environment-variables.md)

## <a name="examples"></a>Przykłady

```cli
nuget update

# update packages installed in solution.sln, using MSBuild version 14.0 to load the solution and its project(s).
nuget update solution.sln -MSBuildVersion 14

nuget update -safe

nuget update -self
```
