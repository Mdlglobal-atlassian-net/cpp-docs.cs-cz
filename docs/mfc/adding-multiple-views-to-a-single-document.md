---
title: Přidání více zobrazení do jednoho dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 593c59c73b58b4364c9d652ce8eb415c17af496c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394738"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Přidání více zobrazení do jednoho dokumentu

V aplikaci SDI (SDI) vytvořené pomocí knihovny Microsoft Foundation Class (MFC) je přidružený k typu jedno zobrazení každý typ dokumentu. V některých případech je třeba mít možnost přepnout aktuální zobrazení dokumentu pomocí nové zobrazení.

> [!TIP]
>  Další postupy při implementaci více zobrazení pro jednotlivý dokument najdete v tématu [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) a [SHROMAŽĎOVAT](../overview/visual-cpp-samples.md) vzorek MFC.

Tuto funkci můžete implementovat přidáním nového `CView`-odvozené třídy a další kód pro přepínání zobrazení dynamicky k existující aplikaci MFC.

Kroky jsou následující:

- [Upravit existující třída aplikace](#vcconmodifyexistingapplicationa1)

- [Vytvoření a úprava nové třídy zobrazení](#vcconnewviewclassa2)

- [Vytvoření a připojení nového zobrazení](#vcconattachnewviewa3)

- [Implementace přepínání – funkce](#vcconswitchingfunctiona4)

- [Přidání podpory pro přepnutí zobrazení](#vcconswitchingtheviewa5)

Zbývající část tohoto tématu se předpokládá následující:

- Název `CWinApp`-odvozeného objektu je `CMyWinApp`, a `CMyWinApp` je deklarovány a definovány v *MYWINAPP. H* a *MYWINAPP. CPP*.

- `CNewView` je název nového `CView`-odvozenému objektu, a `CNewView` je deklarovány a definovány v *NEWVIEW. H* a *NEWVIEW. CPP*.

##  <a name="vcconmodifyexistingapplicationa1"></a> Upravit existující třída aplikace

Pro aplikaci k přepínání mezi zobrazeními budete muset upravit přidáním členské proměnné k uložení zobrazení a způsob, jak je přepnout – třída aplikace.

Přidejte následující kód k deklaraci `CMyWinApp` v *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Nové proměnné členů `m_pOldView` a `m_pNewView`, přejděte na aktuální zobrazení a tak nově vytvořený. Nové metody (`SwitchView`) Přepíná zobrazení při požadavku uživatele. Tělo metody je popsána dále v tomto tématu v [implementovat funkci přepínání](#vcconswitchingfunctiona4).

Poslední změny – třída aplikace vyžaduje, včetně nový soubor hlaviček, který definuje zprávy Windows (**WM_INITIALUPDATE**), který se používá ve funkci přepínání.

Vložte následující řádek v části zahrnout *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Uložte změny a pokračovat k dalšímu kroku.

##  <a name="vcconnewviewclassa2"></a> Vytvoření a úprava nové třídy zobrazení

Vytvoření nové třídy zobrazení je snadné pomocí **novou třídu** příkaz k dispozici v zobrazení tříd. Jediným požadavkem pro tuto třídu je, že se odvozuje od `CView`. Tato nová třída přidáte do aplikace. Konkrétní informace při přidání nové třídy do projektu, naleznete v tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md).

Po přidání třídy do projektu, budete muset změnit přístupnost některé členy třídy zobrazení.

Upravit *NEWVIEW. H* změnou specifikátor přístupu z **chráněné** k **veřejné** pro konstruktor a destruktor. To umožňuje třídě vytvořeno a zničeno při dynamicky a upravit vzhled zobrazení dřív, než bude viditelné.

Uložte změny a pokračovat k dalšímu kroku.

##  <a name="vcconattachnewviewa3"></a> Vytvoření a připojení nového zobrazení

Vytvoření a připojení nového zobrazení, budete muset upravit `InitInstance` funkce třídy aplikace. Úpravy přidá nový kód, který vytvoří nový objekt zobrazení i pak inicializuje `m_pOldView` a `m_pNewView` se dva existující objekty zobrazení.

Protože je vytvořeno nové zobrazení v rámci `InitInstance` funkce, nové i stávající zobrazení zachovat po dobu životnosti aplikace. Ale aplikace stejně snadno vytvořit nové zobrazení dynamicky.

Vložte tento kód po volání `ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Uložte změny a pokračovat k dalšímu kroku.

##  <a name="vcconswitchingfunctiona4"></a> Implementace přepínání – funkce

V předchozím kroku přidáte kód, který je vytvořen a inicializován nový objekt zobrazení. Poslední hlavních součástí je implementovat metodu přepínání `SwitchView`.

Na konci souboru implementace pro vaši aplikaci třídu (*MYWINAPP. CPP*), přidejte následující definici metody:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Uložte změny a pokračovat k dalšímu kroku.

##  <a name="vcconswitchingtheviewa5"></a> Přidání podpory pro přepnutí zobrazení

Poslední krok zahrnuje přidání kódu, který volá `SwitchView` metodu, když aplikace potřebuje k přepínání mezi zobrazeními. To lze provést několika způsoby: Přidání nové položky nabídky pro uživatele k výběru nebo interně přepínání zobrazení při splnění určitých podmínek.

Další informace o přidání nových položek nabídky a funkce obslužné rutiny příkazů najdete v tématu [obslužné rutiny pro příkazy a oznámení ovládacích prvků](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Viz také:

[Document/View – architektura](../mfc/document-view-architecture.md)
