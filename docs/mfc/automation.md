---
title: Automatizace
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: 7818aa708a762f2a284be029a6c3f3facd971d9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374152"
---
# <a name="automation"></a>Automatizace

Automatizace (dříve označované jako automatizace OLE) umožňuje jednu aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo ke zveřejnění objekty, lze manipulovat.

[Automatizační server](../mfc/automation-servers.md) je aplikace (typ serveru COM.), která zpřístupňuje jeho funkce přes rozhraní modelu COM k ostatním aplikacím, volá [klientům automatizace](../mfc/automation-clients.md). Možnost vidět umožňuje klientům služby Automation automatizovat přímo přístup k objektům a používání služeb, které poskytují určité funkce.

Automatizační servery a klienty použijte rozhraní modelu COM, které jsou vždy odvozené z `IDispatch` a používají a vrací konkrétní sadu datových typů, které volá typy ve službě Automation. Můžete automatizovat libovolný objekt, který zpřístupňuje rozhraní automatizace, poskytuje metody a vlastnosti, ke kterým můžete přistupovat z jiných aplikací. Služba Automation je dostupná pro OLE a modelu COM objekty. Automatizované objekt může být místní nebo vzdálené (na jiný počítač přístupný přes síť). proto existují dvě kategorie služby automation:

- Automatizace (místní).

- Vzdálená automatizace (přes síť pomocí modelu Distributed COM a DCOM).

Zveřejnění objekty je vhodné v případě aplikací poskytují funkce, které jsou užitečné k ostatním aplikacím. Například ovládací prvek ActiveX je typ serveru automatizace. Aplikace hostující ovládací prvek ActiveX je klient automatizace ovládacího prvku.

Další příklad – textový procesor může zveřejnit funkčnost kontrolu pravopisu do jiných programů. Vystavení objektů umožňuje dodavatelům ke zlepšení svých aplikací s použitím předdefinované funkce jiných aplikací. Tímto způsobem automatizace platí některé zásady objektově orientovaného programování, jako je například opětovné použití a zapouzdření na úrovni aplikace sami.

Důležitější je podpora, automatizace poskytuje uživatelům a poskytovatelů řešení. Zveřejněním funkčnost aplikace přes běžné, dobře definovaných rozhraní automatizace umožňuje vytvářet komplexní řešení v jediné Obecné programovací jazyk, jako je například Microsoft Visual Basic, ne v různých jazyky – makro specifické pro aplikaci.

Řada obchodních aplikací, jako je například aplikace Microsoft Excel a Microsoft Visual C++, umožňují automatizovat velkou část jejich funkce. Například v jazyce Visual C++ můžete psát makra jazyka VBScript k automatizaci sestavení, aspektů kód, úpravy a ladění úloh.

##  <a name="_core_passing_parameters_in_automation"></a> Předávání parametrů ve službě Automation

Jeden potíže při vytváření metod automatizace pomáhá poskytovat jednotné "bezpečné" mechanismus pro předávání dat mezi automatizační servery a klienty. Použití služby Automation **VARIANT** k předání dat typu. **VARIANT** typ je označený sjednocení. Má datový člen pro hodnotu (to je anonymní sjednocení jazyka C++) a datový člen určující typ informací uložených ve sjednocení. **VARIANT** typů podporuje několik standardních datových typů: 2 a 4bajtová celá čísla, 4 a 8 bajtů s plovoucí desetinnou čárkou čísla, řetězce a logické hodnoty. Kromě toho podporuje **HRESULT** (OLE kódy chyb), **měny** (s pevnou desetinnou čárkou numerický typ), a **datum** (absolutní datum a čas), typy a také odkazy na `IUnknown` a `IDispatch` rozhraní.

**VARIANT** typu, je zapouzdřena v [COleVariant](../mfc/reference/colevariant-class.md) třídy. Podpůrné **měny** a **datum** třídy jsou zapouzdřeny v [COleCurrency](../mfc/reference/colecurrency-class.md) a [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) třídy.

## <a name="automation-samples"></a>Ukázky služby Automation

- [AUTOCLIK](../overview/visual-cpp-samples.md) fungování této ukázky se dozvíte postupy automatizace a jako základ pro výuku vzdálené automatizace.

- [Acdual –](../overview/visual-cpp-samples.md) přidává dvojí rozhraní do aplikaci automatizačního serveru.

- [CALCDRIV](../overview/visual-cpp-samples.md) řízení MFCCALC aplikace klienta automatizace.

- [INPROC](../overview/visual-cpp-samples.md) ukazuje aplikaci automatizačního v procesu serveru.

- [IPDRIVE](../overview/visual-cpp-samples.md) aplikace klienta automatizace řízení INPROC.

- [MFCCALC](../overview/visual-cpp-samples.md) ukazuje aplikace klienta automatizace.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Klienti automatizace](../mfc/automation-clients.md)

- [Automatizační servery](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Technologie Active](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Co chcete udělat

- [Přidejte třídu služby Automation](../mfc/automation-servers.md)

- [Použití knihoven typů](../mfc/automation-clients-using-type-libraries.md)

- [Automatizační servery přístup](../mfc/automation-servers.md)

- [Klienti automatizace napíšeme v jazyce C++](../mfc/automation-clients.md)

## <a name="see-also"></a>Viz také:

[MFC COM](../mfc/mfc-com.md)
