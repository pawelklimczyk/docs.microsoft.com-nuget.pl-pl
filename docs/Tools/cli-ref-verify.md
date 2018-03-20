---
title: "Interfejs wiersza polecenia NuGet Sprawdź polecenie | Dokumentacja firmy Microsoft"
author: dtivel
ms.author: dtivel
manager: doronm
ms.date: 03/06/2018
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Dokumentacja dotycząca nuget.exe Sprawdź polecenie"
keywords: "nuget zweryfikować odwołania, sprawdź, polecenie"
ms.reviewer:
- karann
- rmpablos
ms.openlocfilehash: 096c79670267d9b602dd6ad30640e832441c31c5
ms.sourcegitcommit: 74c21b406302288c158e8ae26057132b12960be8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="verify-command-nuget-cli"></a><span data-ttu-id="53242-104">Sprawdź polecenia (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="53242-104">verify command (NuGet CLI)</span></span>

<span data-ttu-id="53242-105">**Dotyczy:** pakietu zużycie &bullet; **obsługiwane wersje:** 4.6 +</span><span class="sxs-lookup"><span data-stu-id="53242-105">**Applies to:** package consumption &bullet; **Supported versions:** 4.6+</span></span>

<span data-ttu-id="53242-106">Sprawdza, czy pakiet.</span><span class="sxs-lookup"><span data-stu-id="53242-106">Verifies a package.</span></span>

## <a name="usage"></a><span data-ttu-id="53242-107">Użycie</span><span class="sxs-lookup"><span data-stu-id="53242-107">Usage</span></span>

```cli
nuget verify <package(s)> [options]
```

<span data-ttu-id="53242-108">gdzie `<package(s)>` jest co najmniej jeden `.nupkg` plików.</span><span class="sxs-lookup"><span data-stu-id="53242-108">where `<package(s)>` is one or more `.nupkg` files.</span></span>

## <a name="options"></a><span data-ttu-id="53242-109">Opcje</span><span class="sxs-lookup"><span data-stu-id="53242-109">Options</span></span>

| <span data-ttu-id="53242-110">Opcja</span><span class="sxs-lookup"><span data-stu-id="53242-110">Option</span></span> | <span data-ttu-id="53242-111">Opis</span><span class="sxs-lookup"><span data-stu-id="53242-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="53242-112">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="53242-112">All</span></span> | <span data-ttu-id="53242-113">Określa, że wszystkie sprawdzenia możliwe powinien być wykonywany na pakietów.</span><span class="sxs-lookup"><span data-stu-id="53242-113">Specifies that all verifications possible should be performed on the package(s).</span></span> |
| <span data-ttu-id="53242-114">CertificateFingerprint</span><span class="sxs-lookup"><span data-stu-id="53242-114">CertificateFingerprint</span></span> | <span data-ttu-id="53242-115">Określa co najmniej jeden algorytm SHA-256 certyfikatu odciski palców certyfikatów (s), które podpisem pakiety muszą być podpisane przy.</span><span class="sxs-lookup"><span data-stu-id="53242-115">Specifies one or more SHA-256 certificate fingerprints of certificates(s) which signed packages must be signed with.</span></span> <span data-ttu-id="53242-116">Odcisk palca certyfikatu algorytmu SHA-256 jest Skrót SHA-256 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="53242-116">A certificate SHA-256 fingerprint is a SHA-256 hash of the certificate.</span></span> <span data-ttu-id="53242-117">Wielu danych wejściowych powinny być oddzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="53242-117">Multiple inputs should be semicolon separated.</span></span> |
| <span data-ttu-id="53242-118">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="53242-118">ConfigFile</span></span> | <span data-ttu-id="53242-119">Plik konfiguracyjny NuGet do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="53242-119">The NuGet configuration file to apply.</span></span> <span data-ttu-id="53242-120">Jeśli nie zostanie określony, `%AppData%\NuGet\NuGet.Config` (system Windows) lub `~/.nuget/NuGet/NuGet.Config` (system Mac/Linux) jest używany.</span><span class="sxs-lookup"><span data-stu-id="53242-120">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="53242-121">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="53242-121">ForceEnglishOutput</span></span> | <span data-ttu-id="53242-122">Wymusza nuget.exe przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="53242-122">Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="53242-123">Pomoc</span><span class="sxs-lookup"><span data-stu-id="53242-123">Help</span></span> | <span data-ttu-id="53242-124">Wyświetla Pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="53242-124">Displays help information for the command.</span></span> |
| <span data-ttu-id="53242-125">Nieinterakcyjne</span><span class="sxs-lookup"><span data-stu-id="53242-125">NonInteractive</span></span> | <span data-ttu-id="53242-126">Pomija wyświetla monit o dane wejściowe użytkownika lub potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="53242-126">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="53242-127">Podpisy</span><span class="sxs-lookup"><span data-stu-id="53242-127">Signatures</span></span> | <span data-ttu-id="53242-128">Określa, należy wykonać weryfikacji podpisu pakietu.</span><span class="sxs-lookup"><span data-stu-id="53242-128">Specifies that package signature verification should be performed.</span></span> |
| <span data-ttu-id="53242-129">Szczegółowość</span><span class="sxs-lookup"><span data-stu-id="53242-129">Verbosity</span></span> | <span data-ttu-id="53242-130">Określa ilość szczegółów wyświetlanych w danych wyjściowych: *normalne*, *quiet*, *szczegółowe*.</span><span class="sxs-lookup"><span data-stu-id="53242-130">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

## <a name="examples"></a><span data-ttu-id="53242-131">Przykłady</span><span class="sxs-lookup"><span data-stu-id="53242-131">Examples</span></span>

```cli
nuget verify -Signatures .\..\MyPackage.nupkg -CertificateFingerprint "CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039;5F874AAF47BCB268A19357364E7FBB09D6BF9E8A93E1229909AC5CAC865802E2" -Verbosity detailed

nuget verify -Signatures c:\packages\MyPackage.nupkg -CertificateFingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039

nuget verify -Signatures MyPackage.nupkg -Verbosity quiet

nuget verify -Signatures .\*.nupkg
```