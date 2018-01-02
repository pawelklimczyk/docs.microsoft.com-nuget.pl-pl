---
title: "Prefiks Identyfikatora rezerwacji odwołania | Dokumentacja firmy Microsoft"
author: diverdan92
ms.author: diverdan92
manager: unniravindranathan
ms.date: 10/9/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 76c0bb7f-9aaf-4c09-b3fd-f6802f9dd602
description: Opis funkcji rezerwacji prefiks Identyfikatora pakietu i przewodnik autora.
keywords: "Identyfikator pakietu NuGet, prefiks, zastrzeżenia"
ms.reviewer:
- ananguar
- karann-msft
- unniravindranathan
ms.openlocfilehash: e94d1431667ec17347165ac0a3993c0b552e6a60
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="package-id-prefix-reservation"></a>Rezerwacji prefiks Identyfikatora pakietu
[nuget.org](https://www.nuget.org/) i Visual Studio 2017 wersji 15,4 lub nowszej Pokaż visual wskaźnika dla pakietów, które są przesyłane przez właścicieli z prefiksem Identyfikatora pakietu zastrzeżone tak długo, jak pakiet jest zgodny z Identyfikatorem zastrzeżonego prefiksu wzorzec nazewnictwa. Przesunięcie wyjaśniono wymaga rezerwacji prefiks Identyfikatora i jak poprosić właściciela o prefiks Identyfikatora.

## <a name="what-is-package-id-prefix-reservation"></a>Co to jest rezerwacji prefiks Identyfikatora pakietu?
Pakiet właścicieli są w stanie zarezerwować, aby chronić swoją tożsamość przez zarezerwowanie prefiksy identyfikator. Konsumenci pakietu są dostarczane z dodatkowymi informacjami korzystanie z pakietami, które pakiet, w którym są one konsumowania nie są w ich właściwości identyfikujących fałszywych. Zapoznaj się z Zobacz rezerwacji prefiks Identyfikatora działania w szczegółach.

## <a name="id-prefix-reservation-details"></a>Szczegóły rezerwacji prefiks Identyfikatora 
Gdy jest zastrzeżony prefiks Identyfikatora pakietu, ma miejsce na kilka rzeczy [nuget.org](https://www.nuget.org/) galerii, jak również w programie Visual Studio. Ponadto są zaawansowane scenariusze, które są obsługiwane przez zastrzeżenia prefiks Identyfikatora, takie jak ustawienie prefiksu jako "public" delegowanie podzestawy prefiksu do wielu właścicieli.

Poniżej opisano funkcję w szczegółów, a także bardziej zaawansowane funkcje.

### <a name="id-prefix-reservation-on-nugetorg"></a>Identyfikator rezerwacji prefiks na nuget.org
Gdy prefiks jest zarezerwowana na [nuget.org](https://www.nuget.org/), nastąpi następujące:
1. Zastrzeżenie prefiks jest skojarzony z właścicielem lub zbiór właścicieli na [nuget.org](https://www.nuget.org/). 
2. Zawsze, gdy pakiet jest przesyłany do [nuget.org](https://www.nuget.org/) o identyfikatorze, który odpowiada zastrzeżony prefiks Identyfikatora, pakiet zostanie odrzucony, o ile nie pochodzi z jego właściciela, która zastrzeżony prefiks Identyfikatora.
3. Pakiet zgodny zastrzeżony prefiks Identyfikatora i pochodzi z jego właściciela, która zastrzeżony prefiks Identyfikatora będzie mieć visual wskaźnika w wersji Visual Studio 2017 15,4 lub nowszej, a na [nuget.org](https://www.nuget.org/) wskazujący, że pakiet jest w obszarze zastrzeżony prefiks Identyfikatora. Dotyczy to zarówno nowe przesłanych pakietów, jak i istniejące pakiety w jego właściciela. **Uwaga:** wskaźnika w programie Visual Studio będą wyświetlane tylko w przypadku pojedynczego źródła danych jest wybrany jako źródło pakietu. 
4. Wszystkie istniejące pakiety zgodne zastrzeżony prefiks Identyfikatora, ale są *nie* należących do właściciela zarezerwowanego prefiks pozostanie bez zmian (nie będzie nieznajdujące się na liście, ale mogą również mieć visual wskaźnika). Ponadto właścicieli tych pakietów nadal będzie mógł przesłać nowe wersje pakietu.

Te zmiany są oparte na następujących warunkach i nałożyć kilka dodatkowych ograniczeń:
* Tylko jeden właściciel pakietu musi mieć zastrzeżony prefiks visual wskaźnika (w przypadku pakietów z wielu właścicieli) i pojawienie się.
* Jeśli istnieje więcej niż jednego właściciela pakietu, gdy jeden lub więcej właścicieli ma zastrzeżony prefiks i jednego lub więcej właścicieli ma zastrzeżony prefiks, właściciele z zarezerwowanym prefiksem można usunąć inne armatora(-ów) z zarezerwowanym prefiksem. Właścicieli, którzy nie mają zastrzeżony prefiks nie może usunąć właścicieli się od zastrzeżonego prefiksu. Będą oni mogli nadal usunąć inne właścicieli, które nie mają również zastrzeżony prefiks.
  * Pakiet ma wizualne wskaźnika, powinien *zawsze* visual wskaźnik (zagwarantowanie, że co najmniej jeden właściciel z zarezerwowanym prefiksem zawsze będzie właściciela)

### <a name="advanced-prefix-reservation-scenarios"></a>Prefiks zaawansowanych scenariuszy zastrzeżenia
Istnieje kilka bardziej zaawansowanych scenariuszy rezerwacji prefiks opisane poniżej, w tym delegowanie subprefix i prefiksy oznaczanie jako public. Poniżej przedstawiono bardziej zaawansowanych, które można podjąć rezerwacji prefiks. 

* Podczas rezerwacji prefiks właściciela mogą żądać delegowania podzestawy prefiksu (lub prefiks) do innych właścicieli. Na przykład jeśli '[Microsoft](https://www.nuget.org/profiles/microsoft)"właścicielem" firmy Microsoft.\*", ale"[aspnet](https://www.nuget.org/profiles/aspnet)"chce zarezerwować" Microsoft.AspNet.\*","[Microsoft](https://www.nuget.org/profiles/microsoft)"może Wybierz delegować "Microsoft.AspNet. \*"do [aspnet](https://www.nuget.org/profiles/aspnet) konta.
*  Podczas rezerwacji prefiks właściciela można udostępnić prefiksu. Nadal zapewni ich wizualnej pokazujący, że pakiet pochodzi z zarezerwowanym prefiksem, ale będzie **nie** zablokować przesłanych przyszłych pakietu na prefiksie dla dowolnego właściciela. Jest to przydatne w przypadku projektów typu open source z wielu współautorzy — współautorzy top lub core może mieć prefiksu zastrzeżone, ale nadal może być otwarty dla wszystkich uczestników. 

### <a name="prefix-reservation-visual-indicator"></a>Prefiks rezerwacji wizualnej
Jeśli pakiet pochodzi z zastrzeżony prefiks, zobaczy poniżej visual wskaźników [nuget.org](https://www.nuget.org/) galerii w Visual Studio 2017 wersji 15,4 lub nowszej:

**Galeria nuget.org**
![nuget.org galerii](media/nuget-gallery-reserved-prefix.png)

**Visual Studio**
![programu Visual Studio](media/visual-studio-reserved-prefix.png)

## <a name="id-prefix-reservation-application-process"></a>Proces aplikacji rezerwacji prefiks Identyfikatora
Aby zastosować do rezerwacji prefiksu, wykonaj następujące czynności. 
1. Przejrzyj akceptacji [kryteria rezerwacji Identyfikatora prefiks](#id-prefix-reservation-criteria).
2. Określić obszarów nazw do zarezerwowania, oprócz żadnego [zaawansowanych scenariuszy rezerwacji prefiks](#advanced-prefix-reservation-scenarios) może wymagać.
3. Wysyłanie poczty do [ account@nuget.org ](mailto:account@nuget.org) z właścicielem nazwy wyświetlanej na [nuget.org](https://www.nuget.org/), a także wszystkie zastrzeżone prefiksy żądania dostępu. Jeśli prefiks podzestawy są delegowanie do wielu właścicieli, upewnij się, zawierać wszystkie nazwy wyświetlane właściciela i prefiksu podzestawy.

Po przesłaniu aplikacji, użytkownik zostanie powiadomiony o zatwierdzenia lub odrzucenia (za pomocą kryteriów powodujących odrzucenia). Firma Microsoft może być konieczne pytania dodatkowe identyfikujące potwierdzić tożsamość właściciela. 

### <a name="id-prefix-reservation-criteria"></a>Kryterium rezerwacji prefiks Identyfikatora
Podczas przeglądania dowolnej aplikacji dla rezerwacji prefiks Identyfikatora, [nuget.org](https://www.nuget.org/) zespół będzie evalaute aplikacji przed poniżej kryteriów. Nie wszystkie kryteria musi spełnić prefiksu do zarezerwowania, ale aplikacja jest niedozwolony, jeśli nie jest dowód kryteriów spełniane (wraz z wyjaśnieniem, podane):
1. Prefiks Identyfikatora pakietu poprawnie i jasno identyfikuje właściciela pakietu?
2. Czy duża liczba pakietów, które już zostały przesłane przez właściciela, w obszarze prefiks Identyfikatora pakietu?
3. Prefiks Identyfikatora pakietu jest coś wspólnego, które nie powinny należeć do dowolnej poszczególnych właściciel lub organizacja?
4. Czy *nie* rezerwowania prefiks Identyfikatora pakietu powodować niejednoznaczności i nieporozumień wśród społeczności?
5. Czy właściwości identyfikujących pakiety, które odpowiada pakietu prefiks Identyfikatora wyczyść i spójny (szczególnie Autor pakietu)?

## <a name="3rd-party-feed-provider-scenarios"></a>scenariusze dostawcy źródła danych strony 3
Jeśli strona 3 źródła danych dostawcy jest zainteresowana Implementowanie własne usługi, aby umożliwić zastrzeżenia prefiksu, możesz to zrobić, modyfikując źródła danych usługi wyszukiwania w wersji 3 NuGet dostawców. Dodatek do usługi wyszukiwania źródła jest dodanie *zweryfikować* właściwości wraz z przykładami dla źródeł danych w wersji 3 poniżej. Klienta NuGet w wersji 2, źródła danych, nie będzie obsługiwał dodanej właściwości.

Aby uzyskać więcej informacji, zobacz [dokumentację dotyczącą Usługa wyszukiwania w interfejsie API](../api/search-query-service-resource.md).