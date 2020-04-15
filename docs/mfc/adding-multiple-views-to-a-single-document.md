---
title: Přidání více zobrazení do jednoho dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 4fa39a4d9369c84d2cffdaeff28dc9cb2f966b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370858"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Přidání více zobrazení do jednoho dokumentu

V aplikaci rozhraní s jedním dokumentem (SDI) vytvořené pomocí knihovny Microsoft Foundation Class (MFC) je každý typ dokumentu přidružen k typu jednoho zobrazení. V některých případech je žádoucí mít možnost přepnout aktuální zobrazení dokumentu s novým zobrazením.

> [!TIP]
> Další postupy pro implementaci více zobrazení pro jeden dokument naleznete v [tématu CDocument::AddView](../mfc/reference/cdocument-class.md#addview) a [collect](../overview/visual-cpp-samples.md) mfc ukázka.

Tuto funkci můžete implementovat přidáním nové `CView`odvozené třídy a dalšího kódu pro dynamické přepnutí zobrazení do existující aplikace knihovny MFC.

Kroky jsou následující:

- [Upravit existující třídu aplikace](#vcconmodifyexistingapplicationa1)

- [Vytvoření a úprava nové třídy zobrazení](#vcconnewviewclassa2)

- [Vytvoření a připojení nového zobrazení](#vcconattachnewviewa3)

- [Implementace funkce přepínání](#vcconswitchingfunctiona4)

- [Přidání podpory pro přepínání zobrazení](#vcconswitchingtheviewa5)

Zbývající část tohoto tématu předpokládá následující:

- Název `CWinApp`-derived objekt je `CMyWinApp`a `CMyWinApp` je deklarován a definován v *MYWINAPP. H* a *MYWINAPP. CPP*.

- `CNewView`je název nového `CView`odvozeného objektu `CNewView` a je deklarován a definován v *NEWVIEW. H* a *NEWVIEW. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Upravit existující třídu aplikace

Aby aplikace přepínala mezi zobrazeními, je třeba upravit třídu aplikace přidáním členských proměnných pro uložení zobrazení a metodu pro jejich přepnutí.

Do deklarace `CMyWinApp` v *MYWINAPP přidejte následující kód. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Nové členské proměnné `m_pOldView` a `m_pNewView`, přejděte na aktuální a nově vytvořené zobrazení. Nová metoda`SwitchView`( ) přepne zobrazení na žádost uživatele. Tělo metody je popsáno dále v tomto tématu v [implementovat spínací funkce](#vcconswitchingfunctiona4).

Poslední změna třídy aplikace vyžaduje zahrnutí nového souboru záhlaví, který definuje zprávu systému Windows **(WM_INITIALUPDATE),** která se používá ve funkci přepínání.

Vložte následující řádek do části zahrnout *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Uložte změny a pokračujte dalším krokem.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Vytvoření a úprava nové třídy zobrazení

Vytvoření nové třídy zobrazení je snadné pomocí příkazu **Nová třída,** který je k dispozici ze zobrazení třídy. Jediným požadavkem pro tuto třídu `CView`je, že je odvozen od . Přidejte tuto novou třídu do aplikace. Konkrétní informace o přidání nové třídy do projektu naleznete v [tématu Přidání třídy](../ide/adding-a-class-visual-cpp.md).

Po přidání třídy do projektu je třeba změnit přístupnost některých členů třídy zobrazení.

Upravte *NEWVIEW. H* změnou specifikátoru přístupu z **chráněného** na **veřejné** pro konstruktor a destruktor. To umožňuje dynamicky vytvářet a ničit třídu a upravovat vzhled zobrazení dříve, než je viditelný.

Uložte změny a pokračujte dalším krokem.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Vytvoření a připojení nového zobrazení

Chcete-li vytvořit a připojit nové zobrazení, je třeba upravit `InitInstance` funkci třídy aplikace. Změna přidá nový kód, který vytvoří nový objekt zobrazení `m_pOldView` `m_pNewView` a potom inicializuje oba i se dvěma existujícími objekty zobrazení.

Vzhledem k tomu, `InitInstance` že nové zobrazení je vytvořen v rámci funkce, nové i existující zobrazení přetrvávají po dobu životnosti aplikace. Aplikace však může stejně snadno vytvořit nové zobrazení dynamicky.

Vložte tento kód `ProcessShellCommand`po volání :

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Uložte změny a pokračujte dalším krokem.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Implementace funkce přepínání

V předchozím kroku jste přidali kód, který vytvořil a inicializoval nový objekt zobrazení. Posledním velkým kusem je implementace metody `SwitchView`přepínání .

Na konci implementačního souboru pro vaši třídu aplikace *(MYWINAPP. CPP*), přidejte následující definici metody:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Uložte změny a pokračujte dalším krokem.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Přidání podpory pro přepínání zobrazení

Poslední krok zahrnuje přidání kódu, který volá metodu, `SwitchView` když aplikace potřebuje přepínat mezi zobrazeními. To lze provést několika způsoby: přidáním nové položky nabídky pro uživatele, aby si mohl vybrat, nebo přepnutím zobrazení interně, pokud jsou splněny určité podmínky.

Další informace o přidávání nových položek nabídky a funkcí obslužné rutiny příkazů naleznete v [tématu Obslužné rutiny pro příkazy a oznámení ovládacího prvku](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Viz také

[Architektura dokumentu/zobrazení](../mfc/document-view-architecture.md)
