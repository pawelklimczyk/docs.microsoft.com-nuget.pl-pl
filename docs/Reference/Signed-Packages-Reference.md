---
title: "Podpisane pakiety odwołania | Dokumentacja firmy Microsoft"
author: rido-min
ms.author: rido-min
manager: unniravindranathan
ms.date: 03/06/2018
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Podpisana opis funkcji pakietów."
keywords: Znak pakietu NuGet, podpisu certyfikatu
ms.reviewer:
- ananguar
- karann-msft
- unniravindranathan
ms.openlocfilehash: 9bf9885aaf42bedb681a5d916202fa8b26749a0c
ms.sourcegitcommit: 74c21b406302288c158e8ae26057132b12960be8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="signed-packages"></a><span data-ttu-id="e9c22-104">Pakiety podpisem</span><span class="sxs-lookup"><span data-stu-id="e9c22-104">Signed packages</span></span>

<span data-ttu-id="e9c22-105">*NuGet 4.6.0+ i Visual Studio 2017 wersji 15.6 i nowsze*</span><span class="sxs-lookup"><span data-stu-id="e9c22-105">*NuGet 4.6.0+ and Visual Studio 2017 version 15.6 and later*</span></span>

<span data-ttu-id="e9c22-106">Pakiety NuGet mogą zawierać podpis cyfrowy, który zapewnia ochronę przed zmodyfikowany zawartości.</span><span class="sxs-lookup"><span data-stu-id="e9c22-106">NuGet packages can include a digital signature that provides protection against tampered content.</span></span> <span data-ttu-id="e9c22-107">Ta sygnatura jest tworzony z certyfikatu X.509, który dodaje również dowody autentyczności do rzeczywistego źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="e9c22-107">This signature is produced from an X.509 certificate that also adds authenticity proofs to the actual origin of the package.</span></span>

<span data-ttu-id="e9c22-108">Pakiety podpisem udostępnienia najwyższy weryfikacji end-to-end.</span><span class="sxs-lookup"><span data-stu-id="e9c22-108">Signed packages provide the strongest end-to-end validation.</span></span> <span data-ttu-id="e9c22-109">Autor podpis gwarantuje, że pakiet nie został zmodyfikowany od czasu autora podpisania pakietu, niezależnie od którego repozytorium lub co metoda jest dostarczany pakiet transportu.</span><span class="sxs-lookup"><span data-stu-id="e9c22-109">An author signature guarantees that the package has not been modified since the author signed the package, no matter from which repository or what transport method the package is delivered.</span></span>

<span data-ttu-id="e9c22-110">Użytkowników potrzebujących środowisku zablokowany może wymagać pakiety podpisane przy użyciu certyfikatu określonego autora.</span><span class="sxs-lookup"><span data-stu-id="e9c22-110">Consumers who demand a locked-down environment can require packages signed with a specific author certificate.</span></span>

<span data-ttu-id="e9c22-111">Ponadto pakiety podpisane przez autora udostępniają mechanizm uwierzytelniania dodatkowego do potoku publikowania nuget.org, ponieważ certyfikat podpisywania musi być zarejestrowana wcześniejsze.</span><span class="sxs-lookup"><span data-stu-id="e9c22-111">Additionally, author-signed packages provide an extra authentication mechanism to the nuget.org publishing pipeline because the signing certificate must be registered ahead of time.</span></span>

<span data-ttu-id="e9c22-112">Aby uzyskać więcej informacji na temat tworzenia podpisanego pakietu, zobacz [podpisywania pakietów](../create-packages/Sign-a-package.md) i [polecenia nuget znak](../tools/cli-ref-sign.md).</span><span class="sxs-lookup"><span data-stu-id="e9c22-112">For details on creating a signed package, see [Signing Packages](../create-packages/Sign-a-package.md) and the [nuget sign command](../tools/cli-ref-sign.md).</span></span>

> [!Important]
> <span data-ttu-id="e9c22-113">nuget.org nie akceptuje obecnie podpisanych pakietów.</span><span class="sxs-lookup"><span data-stu-id="e9c22-113">nuget.org does not presently accept signed packages.</span></span> <span data-ttu-id="e9c22-114">Możesz zarejestrować pakietów do publikowania do niestandardowych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="e9c22-114">You can sign packages for publishing to custom feeds.</span></span>

## <a name="certificate-requirements"></a><span data-ttu-id="e9c22-115">Wymagania certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9c22-115">Certificate requirements</span></span>

<span data-ttu-id="e9c22-116">Podpisywanie pakietu wymaga podpisywania certyfikatu, który jest specjalny typ certyfikatu, który jest prawidłowy dla kodu `id-kp-codeSigning` cel [[RFC 5280 sekcji 4.2.1.12](https://tools.ietf.org/html/rfc5280#section-4.2.1.12)].</span><span class="sxs-lookup"><span data-stu-id="e9c22-116">Package signing requires a code signing certificate, which is a special type of certificate that is valid for the `id-kp-codeSigning` purpose [[RFC 5280 section 4.2.1.12](https://tools.ietf.org/html/rfc5280#section-4.2.1.12)].</span></span> <span data-ttu-id="e9c22-117">Ponadto certyfikat musi mieć publiczny długość klucza RSA 2048 bitów lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="e9c22-117">Additionally, the certificate must have an RSA public key length of 2048 bits or higher.</span></span>

## <a name="get-a-code-signing-certificate"></a><span data-ttu-id="e9c22-118">Uzyskaj certyfikat podpisywania kodu</span><span class="sxs-lookup"><span data-stu-id="e9c22-118">Get a code signing certificate</span></span>

<span data-ttu-id="e9c22-119">Prawidłowe certyfikaty mogą być uzyskane z urzędów certyfikacji publicznej, takich jak:</span><span class="sxs-lookup"><span data-stu-id="e9c22-119">Valid certificates may be obtained from public certificate authorities like:</span></span>

- [<span data-ttu-id="e9c22-120">Symantec</span><span class="sxs-lookup"><span data-stu-id="e9c22-120">Symantec</span></span>](https://trustcenter.websecurity.symantec.com/process/trust/productOptions?productType=SoftwareValidationClass3)
- [<span data-ttu-id="e9c22-121">DigiCert</span><span class="sxs-lookup"><span data-stu-id="e9c22-121">DigiCert</span></span>](https://www.digicert.com/code-signing/)
- [<span data-ttu-id="e9c22-122">Go Daddy</span><span class="sxs-lookup"><span data-stu-id="e9c22-122">Go Daddy</span></span>](https://www.godaddy.com/web-security/code-signing-certificate)
- [<span data-ttu-id="e9c22-123">Globalne logowania</span><span class="sxs-lookup"><span data-stu-id="e9c22-123">Global Sign</span></span>](https://www.globalsign.com/en/code-signing-certificate/)
- [<span data-ttu-id="e9c22-124">Comodo</span><span class="sxs-lookup"><span data-stu-id="e9c22-124">Comodo</span></span>](https://www.comodo.com/e-commerce/code-signing/code-signing-certificate.php)
- [<span data-ttu-id="e9c22-125">Certum</span><span class="sxs-lookup"><span data-stu-id="e9c22-125">Certum</span></span>](https://www.certum.eu/certum/cert,offer_en_open_source_cs.xml) 

<span data-ttu-id="e9c22-126">Pełna lista urzędów certyfikacji ufa systemu Windows można uzyskać z [ http://aka.ms/trustcertpartners ](http://aka.ms/trustcertpartners).</span><span class="sxs-lookup"><span data-stu-id="e9c22-126">The complete list of certification authorities trusted by Windows can be obtained from [http://aka.ms/trustcertpartners](http://aka.ms/trustcertpartners).</span></span>

## <a name="create-a-test-certificate"></a><span data-ttu-id="e9c22-127">Tworzenie certyfikatu testowego</span><span class="sxs-lookup"><span data-stu-id="e9c22-127">Create a test certificate</span></span>

<span data-ttu-id="e9c22-128">Wystawiony samodzielnie Certyfikaty służy do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="e9c22-128">You can use self-issued certificates for testing purposes.</span></span> <span data-ttu-id="e9c22-129">Aby utworzyć certyfikat wystawiony samodzielnie, użyj [SelfSignedCertificate nowy](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate) polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9c22-129">To create a self-issued certificate, use the [New-SelfSignedCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate) PowerShell command.</span></span>

```ps
New-SelfSignedCertificate -Subject "CN=NuGet Test Developer, OU=Use for testing purposes ONLY" `
                          -FriendlyName "NuGetTestDeveloper" `
                          -Type CodeSigning `
                          -KeyUsage DigitalSignature `
                          -KeyLength 2048 `
                          -KeyAlgorithm RSA `
                          -HashAlgorithm SHA256 `
                          -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" `
                          -CertStoreLocation "Cert:\CurrentUser\My" 
```

<span data-ttu-id="e9c22-130">To polecenie tworzy testowania dostępny certyfikat w magazynie certyfikatów osobistych bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e9c22-130">This command creates a testing certificate available in the current user's personal certificate store.</span></span> <span data-ttu-id="e9c22-131">Można otworzyć magazynu certyfikatów, uruchamiając `certmgr.msc` wyświetlić nowo utworzony certyfikat.</span><span class="sxs-lookup"><span data-stu-id="e9c22-131">You can open the certificate store by running `certmgr.msc` to see the newly created certificate.</span></span>

## <a name="timestamp-requirements"></a><span data-ttu-id="e9c22-132">Wymagania dotyczące sygnatury czasowej</span><span class="sxs-lookup"><span data-stu-id="e9c22-132">Timestamp requirements</span></span>

<span data-ttu-id="e9c22-133">Pakiety podpisem powinna zawierać znaczników czasu RFC 3161 do zapewnienia walidacji podpisu poza okres ważności certyfikatu podpisywania pakietu.</span><span class="sxs-lookup"><span data-stu-id="e9c22-133">Signed packages should include an RFC 3161 timestamp to ensure signature validity beyond the package signing certificate's validity period.</span></span> <span data-ttu-id="e9c22-134">Certyfikat używany do podpisywania sygnatura czasowa musi być prawidłowy dla `id-kp-timeStamping` cel [[RFC 5280 sekcji 4.2.1.12](https://tools.ietf.org/html/rfc5280#section-4.2.1.12)].</span><span class="sxs-lookup"><span data-stu-id="e9c22-134">The certificate used to sign the timestamp must be valid for the `id-kp-timeStamping` purpose [[RFC 5280 section 4.2.1.12](https://tools.ietf.org/html/rfc5280#section-4.2.1.12)].</span></span> <span data-ttu-id="e9c22-135">Ponadto certyfikat musi mieć publiczny długość klucza RSA 2048 bitów lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="e9c22-135">Additionally, the certificate must have an RSA public key length of 2048 bits or higher.</span></span>

<span data-ttu-id="e9c22-136">Dodatkowe szczegóły techniczne można znaleźć w [specyfikacji technicznej podpisu pakietu](https://github.com/NuGet/Home/wiki/Package-Signatures-Technical-Details) (GitHub).</span><span class="sxs-lookup"><span data-stu-id="e9c22-136">Additional technical details can be found in the [package signature technical specs](https://github.com/NuGet/Home/wiki/Package-Signatures-Technical-Details) (GitHub).</span></span>