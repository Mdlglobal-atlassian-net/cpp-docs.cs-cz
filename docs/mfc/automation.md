---
title: Automation
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
ms.openlocfilehash: e9320ccf7a21c6110c51366fa8af96596512a4a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370828"
---
# <a name="automation"></a>Automation

Automatizace (dříve označované jako AUTOMATIZACE OLE) umožňuje jedné aplikaci manipulovat s objekty implementovanými v jiné aplikaci nebo vystavit objekty tak, aby s nimi bylo možné manipulovat.

[Automatizační server](../mfc/automation-servers.md) je aplikace (typ serveru COM), která zpřístupňuje své funkce prostřednictvím rozhraní COM jiným aplikacím nazývaným [klienti Automatizace](../mfc/automation-clients.md). Expozice umožňuje klientům automatizace automatizovat určité funkce přímým přístupem k objektům a pomocí služeb, které poskytují.

Automatizační servery a klienti používají rozhraní `IDispatch` COM, která jsou vždy odvozena od a přebírají a vracejí určitou sadu datových typů s názvem Typy automatizace. Můžete automatizovat libovolný objekt, který zpřístupňuje rozhraní automatizace, poskytuje metody a vlastnosti, které můžete přistupovat z jiných aplikací. Automatizace je k dispozici pro objekty OLE i COM. Automatizovaný objekt může být místní nebo vzdálený (v jiném počítači přístupném v síti); proto existují dvě kategorie automatizace:

- Automatizace (místní).

- Vzdálená automatizace (v síti, pomocí distribuovaného modelu COM nebo modelu DCOM).

Vystavení objektů je výhodné, když aplikace poskytují funkce užitečné pro jiné aplikace. Ovládací prvek ActiveX je například typ serveru automatizace. aplikace hostující ovládací prvek ActiveX je automatizačním klientem tohoto ovládacího prvku.

Jako další příklad může textový procesor vystavit své funkce kontroly pravopisu jiným programům. Expozice objektů umožňuje dodavatelům zlepšit jejich aplikace pomocí připravených funkcí jiných aplikací. Tímto způsobem automatizace používá některé zásady objektově orientovaného programování, jako je například opětovné použití a zapouzdření, na úrovni samotných aplikací.

Důležitější je podpora, kterou automatizace poskytuje uživatelům a poskytovatelům řešení. Vystavením funkce aplikace prostřednictvím společného, dobře definovanérozhraní automatizace umožňuje vytvářet komplexní řešení v jednom obecném programovacím jazyce, jako je například Microsoft Visual Basic, namísto v různých jazycích maker specifické pro aplikaci.

Mnoho komerčních aplikací, jako je například Microsoft Excel a Microsoft Visual C++, umožňuje automatizovat většinu jejich funkcí. Například v jazyce Visual C++ můžete zapisovat makra Jazyka VBScript pro automatizaci sestavení, aspektů úprav kódu nebo ladicích úloh.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a>Předávání parametrů v automatizaci

Jedním z problémů při vytváření metod automatizace pomáhá poskytovat jednotný "bezpečný" mechanismus pro přenos dat mezi automatizačními servery a klienty. Automatizace používá **typ VARIANT** k předání dat. Typ **VARIANT** je tagované unie. Má datový člen pro hodnotu (jedná se o anonymní sjednocení jazyka C++ a datový člen označující typ informací uložených v unii. Typ **VARIANT** podporuje řadu standardních datových typů: 2 bajtová a čtyřbajtová celá čísla, čísla s plovoucí desetinnou desetinnou hodnotou 4 a 8 bajtů, řetězce a logické hodnoty. Kromě toho podporuje typy **chyb HRESULT** (OLE), **MĚNY** (číselný typ s pevnou bodem) a **DATE** (absolutní datum a čas) a také ukazatele a `IUnknown` `IDispatch` rozhraní.

Typ **VARIANT** je zapouzdřen ve třídě [COleVariant.](../mfc/reference/colevariant-class.md) Podpůrné **třídy CURRENCY** a **DATE** jsou zapouzdřeny ve třídách [COleCurrency](../mfc/reference/colecurrency-class.md) a [COleDateTime.](../atl-mfc-shared/reference/coledatetime-class.md)

## <a name="automation-samples"></a>Ukázky automatizace

- [AUTOCLIK](../overview/visual-cpp-samples.md) Tato ukázka slouží k naučte se automatizační techniky a jako základ pro učení vzdálené automatizace.

- [ACDUAL](../overview/visual-cpp-samples.md) Přidá do aplikace serveru Automation duální rozhraní.

- [CALCDRIV](../overview/visual-cpp-samples.md) Klientská aplikace automatizace pohánějím MFCCALC.

- [INPROC](../overview/visual-cpp-samples.md) Ukazuje serverovou aplikaci in-process automation.

- [PROTOKOL IPDRIVE](../overview/visual-cpp-samples.md) Automatizace klientské aplikace řízení INPROC.

- [MFCCALC](../overview/visual-cpp-samples.md) Demonstruje klientskou aplikaci automatizace.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Klienti automatizace](../mfc/automation-clients.md)

- [Automatizační servery](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Aktivní technologie](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Co chcete dělat

- [Přidání třídy Automatizace](../mfc/automation-servers.md)

- [Použití knihoven typů](../mfc/automation-clients-using-type-libraries.md)

- [Přístup k automatizačním serverům](../mfc/automation-servers.md)

- [Zapsat klienty automatizace v jazyce C++](../mfc/automation-clients.md)

## <a name="see-also"></a>Viz také

[MFC COM](../mfc/mfc-com.md)
