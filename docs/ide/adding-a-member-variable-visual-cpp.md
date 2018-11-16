---
title: Přidání členské proměnné
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: 2a519c0606a7df6e0ce55997a055d78865afafbf
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694410"
---
# <a name="add-a-member-variable"></a>Přidání členské proměnné

Můžete přidat členské proměnné třídy pomocí zobrazení tříd. Členské proměnné může být buď pro [výměny dat a ověřování dat](../mfc/dialog-data-exchange-and-validation.md), nebo mohou být obecné. Průvodce data členské proměnné slouží k provést příslušné informace a použít ho ke vkládání prvků ve zdrojových souborech na příslušných místech. Můžete členské proměnné z přidat [editoru dialogového okna](../windows/dialog-editor.md) v [zobrazení prostředků](../windows/resource-view-window.md), nebo z [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Při navrhování a implementace dialogového okna, může pro vás výhodnější používat dialogové okno editor k přidávání ovládacích prvků dialogového okna pole a potom implementovat ovládací prvky členské proměnné.

**Přidání členské proměnné pro ovládací prvek dialogového okna v okně zobrazení prostředků pomocí Průvodce přidáním členské proměnné:**

1. V okně zobrazení prostředků rozbalte uzel projektu a uzel dialogové okno k zobrazení seznamu projektu dialogových oknech.

1. Dvakrát klikněte na panel dialogových oken, ke kterému chcete přidat členskou proměnnou a otevře se v editoru dialogového okna.

1. V dialogovém okně zobrazí v editoru dialogového okna klikněte pravým tlačítkem na ovládací prvek, ke kterému chcete přidat členskou proměnnou.

1. V místní nabídce zvolte **přidat proměnnou** zobrazíte [proměnné Průvodce přidáním členské](#add-member-variable-wizard).

   > [!NOTE]
   > Výchozí hodnota je již součástí **ID ovládacího prvku**.

1. Zadání informací do polí příslušné průvodce. Další informace najdete v tématu [ovládací prvky dialogového okna a typy proměnných](#dialog-box-controls-and-variable-types).

1. Vyberte **Dokončit** definice a implementace kódu přidejte do projektu a zavřete průvodce.

**Přidání členské proměnné ze zobrazení tříd pomocí Průvodce přidáním členské proměnné:**

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), rozbalte uzel projektu pro zobrazení tříd v projektu.

1. Klikněte pravým tlačítkem na třídu, ke kterému chcete přidat proměnnou.

1. V místní nabídce zvolte **přidat**a klikněte na tlačítko **přidat proměnnou** zobrazíte Průvodce přidáním členské proměnné.

1. Zadání informací do polí příslušné průvodce. Další informace najdete v tématu [proměnné Průvodce přidáním členské](#add-member-variable-wizard).

1. Vyberte **Dokončit** definice a implementace kódu přidejte do projektu a zavřete průvodce.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce přidáním členské proměnné](#add-member-variable-wizard)
- [Ovládací prvky dialogového okna a typy proměnných](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>Průvodce přidáním členské proměnné

Tento průvodce přidá deklaraci členské proměnné do souboru hlaviček. V závislosti na možnostech ho můžete přidat kód do souboru .cpp. Po přidání členské proměnné pomocí průvodce, můžete upravit kód ve vývojovém prostředí.

- **Přístup**

  Nastaví přístup k členské proměnné. Modifikátory přístupu jsou klíčová slova, které určují přístup jiných tříd k členské proměnné. Další informace o zadávání přístup, najdete v části [řízení přístupu členů](../cpp/member-access-control-cpp.md). Úroveň přístup k proměnným členů je nastavena na `public` ve výchozím nastavení.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **Typ proměnné**

  Nastaví návratový typ pro členské proměnné, kterou chcete přidat.

  - Pokud přidáváte členské proměnné, která není ovládací prvek dialogového okna, vyberte ze seznamu dostupných typů.

    Informace o typech najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

    |||
    |-|-|
    |`char`|`short`|
    |`double`|`unsigned char`|
    |`float`|`unsigned int`|
    |`int`|`unsigned long`|
    |`long`||

  - Pokud přidáváte členské proměnné pro ovládací prvek dialogového okna, je toto pole vyplněna typu objektu, který je vrácen pro ovládací prvek nebo hodnotu. Pokud vyberete **ovládací prvek**, pak **typ proměnné** určuje základní třídu vyberete ovládací prvek **ID ovládacího prvku** pole. Pokud ovládací prvek dialogového okna pole může obsahovat hodnotu, a pokud vyberete **hodnotu**, pak **typ proměnné** určuje odpovídající typ hodnoty, které může obsahovat ovládací prvek. Další informace najdete v tématu [ovládací prvky dialogového okna a typy proměnných](#dialog-box-controls-and-variable-types).

    Tato hodnota závisí na výběr v **ID ovládacího prvku** a nedá se změnit.

- **Název proměnné**

  Nastaví název členské proměnné, kterou chcete přidat. Členské proměnné obvykle začínají identifikační řetězec `m_`, který je zadaný pro vás ve výchozím nastavení.

- **Proměnné ovládacího prvku.**

  Označuje, že spravuje členskou proměnnou ovládacího prvku dialogové okno s [výměny dat a ověřování dat](../mfc/dialog-data-exchange-and-validation.md) podporovat. Další informace najdete v tématu [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange). Tato možnost je dostupná jenom pro členské proměnné přidány do třídy odvozené od [CDialog](../mfc/reference/cdialog-class.md). Zaškrtněte toto políčko, chcete-li aktivovat **ID ovládacího prvku** a **ovládací prvek typu** možnosti.

- **ID ovládacího prvku**

  Nastaví ID pro ovládací prvek proměnnou, kterou přidáváte. Vyberte ze seznamu ID pro typ ovládacího prvku, pro kterou přidáváte členské proměnné. V seznamu je účinné pouze tehdy, když **řídicí proměnná** je zaškrtnuté políčko, a to je omezená na ID pro ovládací prvky již přidán do dialogového okna. Například pro standardní **OK** je ID ovládacího prvku tlačítko, **IDOK**.

  |Možnost|Popis|
  |------------|-----------------|
  |**Ovládací prvek**|Tato možnost je nastavena ve výchozím nastavení pro typ ovládacího prvku. Spravuje samotný ovládací prvek, není stav nebo obsah ovládacího prvku (jak je můžete chtít spravovat pro seznam, pole se seznamem nebo upravit).|
  |**Hodnota**|Tato možnost je dostupná pro typy ovládacích prvků, které mohou obsahovat hodnotu nebo zobrazit stav, jako je například do textového pole nebo zaškrtněte políčko. Je také k dispozici pro typy ovládacích prvků, pro které může spravovat rozsahu, obsah nebo stavu. Další informace najdete v tématu [ovládací prvky dialogového okna a typy proměnných](#dialog-box-controls-and-variable-types).|

- **Kategorie**

  Určuje, zda je proměnná založená na typu ovládacího prvku nebo hodnota ovládacího prvku.

- **Typ ovládacího prvku**

  Nastaví typ ovládacího prvku přidán. Toto políčko není možné změnit. Například, že tlačítko má typ ovládacího prvku **tlačítko**, a má typ ovládacího prvku pole se seznamem **– pole se SEZNAMEM**. Další informace najdete v tématu [ovládací prvky dialogového okna a typy proměnných](#dialog-box-controls-and-variable-types).

- **Maximální počet znaků**

  K dispozici pouze tehdy, když **typ proměnné** je nastavena na [CString](../atl-mfc-shared/reference/cstringt-class.md). Určuje největší počet znaků, které může obsahovat ovládací prvek.

- **Minimální hodnota**

  K dispozici pouze v případě, že je typ proměnné `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, [COLECurrency](../mfc/reference/colecurrency-class.md)nebo [CTime](../atl-mfc-shared/reference/ctime-class.md). Určuje přijatelné pro změnu nebo rozsah nejnižší hodnotu.

- **Maximální hodnota**

  K dispozici pouze v případě, že je typ proměnné `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, `COLECurrency`, nebo `CTime`. Určuje přijatelné pro změnu nebo rozsah nejvyšší hodnotu.

- **soubor .h**

  Pro ovládací prvky ActiveX, jejíž členské proměnné vyžadují obálkovou třídu. Nastaví název souboru hlavičky k přidání deklarace třídy.

- **soubor .cpp**

  Pro ovládací prvky ActiveX, jejíž členské proměnné vyžadují obálkovou třídu. Nastaví název implementačního souboru přidat definici třídy.

- **Komentář**

  Komentář v souboru hlaviček pro členské proměnné.

## <a name="dialog-box-controls-and-variable-types"></a>Ovládací prvky dialogového okna a typy proměnných

Můžete použít [Průvodce přidáním členské proměnné](#add-member-variable-wizard) přidání členské proměnné do ovládacího prvku dialogu pole vytvořené pomocí knihovny MFC. Typ ovládacího prvku, pro který přidáte členské proměnné určuje možnosti, které se zobrazí v dialogovém okně.

Následující tabulka popisuje všechny dialogové okno typy ovládacích prvků, které jsou podporovány v prostředí MFC a [editoru dialogového okna](../windows/dialog-editor.md). Zobrazí také jejich dostupné typy a hodnoty.

|Ovládací prvek|Typ ovládacího prvku|Typ řídicí proměnné|Typ hodnoty proměnné|Minimální/maximální hodnoty (pouze typ hodnoty)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Animace ovládacího prvku|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Tlačítko|TLAČÍTKO|[CButton](../mfc/reference/cbutton-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Zaškrtávací políčko|KONTROLA|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|Minimální hodnota/maximální hodnoty|
|Pole se seznamem|POLE SE SEZNAMEM|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString –](../atl-mfc-shared/reference/cstringt-class.md)|Maximální počet znaků|
|Ovládací prvek pro výběr data|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime –](../atl-mfc-shared/reference/ctime-class.md)|Minimální hodnota/maximální hodnoty|
|Textové pole|UPRAVIT|[Cedit –](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime`, nebo `COleCurrency`|Minimální hodnota/maximální hodnoty; maximální počet znaků: některé podpory|
|Ovládacího prvku klávesová zkratka|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Pole se seznamem|LISTBOX|[Clistbox –](../mfc/reference/clistbox-class.md)|`CString`|Maximální počet znaků|
|Ovládací prvek seznamu|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládací prvek měsíční kalendář|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Minimální hodnota/maximální hodnoty|
|Ovládací prvek průběh|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládacího prvku Rich Edit 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maximální počet znaků|
|Ovládací prvek pro úpravy s formátováním|RICHEDIT|`CRichEditCtrl`|`CString`|Maximální počet znaků|
|Posuvník (svislý nebo vodorovný|POSUVNÍK|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Minimální hodnota/maximální hodnoty|
|Posuvník|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Minimální hodnota/maximální hodnoty|
|Ovládací prvek typu číselník|msctls_updown32|[Cspinbuttonctrl –](../mfc/reference/cspinbuttonctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládací prvek karty|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládací prvek stromu|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
