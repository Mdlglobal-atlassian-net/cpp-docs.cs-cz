---
title: Úprava tabulek akcelerátorů (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 56e24efb-d06b-4ed9-8915-1f99f725e247
ms.openlocfilehash: dfa0c26132378bcbe8a7f5203351134d91746aa7
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232172"
---
# <a name="editing-accelerator-tables-c"></a>Úprava tabulek akcelerátorů (C++)

V projektu v jazyce C++ můžete upravit přímo s místní úpravy. v tabulky akcelerátorů **akcelerátoru** editoru.

Použití standardních stránkách vlastností najdete v níže uvedených postupech, ale úpravy na místě a metoda stránka Vlastnosti mít stejný výsledek. Změny provedené pomocí stránky vlastností nebo pomocí úpravy na místě se okamžitě projeví v tabulce akcelerátorů.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-edit-in-an-accelerator-table"></a>Úprava v tabulce akcelerátorů

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte položku v tabulce a vybrat, zda chcete aktivovat místní úpravy.

1. Vyberte z rozevíracího seznamu nebo zadejte místo, kde můžete provádět změny.

   - Pro [ID](id-property.md), vyberte ze seznamu nebo typu, který chcete upravit.

   - Pro [modifikátor](../windows/accelerator-modifier-property.md), vyberte ze seznamu.

   - Pro [klíč](../windows/accelerator-key-property.md), vyberte ze seznamu nebo typu, který chcete upravit.

   - Pro [typ](../windows/accelerator-type-property.md)vyberte **ASCII** nebo **VIRTKEY** ze seznamu.

## <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Chcete-li najít záznam v tabulce akcelerátorů otevřít

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte sloupec head k řazení obsahu sloupce podle abecedy. Vyberte například **ID** zobrazíte všechna ID v tabulce akcelerátorů podle abecedy.

Potom můžete vyhledat v seznamu a vyhledejte položku.

## <a name="to-add-an-entry-to-an-accelerator-table"></a>Přidání záznamu do tabulky akcelerátorů

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Klikněte pravým tlačítkem v tabulce akcelerátorů a zvolte **nový akcelerátor** z místní nabídky, nebo vyberte položku prázdný řádek v tabulce dole.

1. Vyberte [ID](id-property.md) z rozevíracího seznamu v ID pole nebo zadejte nové ID v **ID** pole.

1. Typ [klíč](../windows/accelerator-key-property.md) chcete použít jako akcelerátor nebo klikněte pravým tlačítkem a zvolte **další stisknutá klávesa** z místní nabídky k nastavení kombinace kláves ( **další stisknutá klávesa** je příkaz k dispozici prostřednictvím **upravit** nabídky).

1. Změnit [modifikátor](../windows/accelerator-modifier-property.md) a [typ](../windows/accelerator-type-property.md), v případě potřeby.

1. Stisknutím klávesy **zadejte**.

   > [!NOTE]
   > Ujistěte se, že se všechny akcelerátory, které definujete. Může mít několik kombinace kláves, které jsou přiřazeny stejnému identifikátoru s neplatí výplně, například **Ctrl** + **P** a **F8** lze obě přiřadit ID_PRINT. Však mít přiřazeno více než jeden ID nebude fungovat dobře, například kombinaci kláves **Ctrl** + **Z** přiřazená ID_SPELL_CHECK a ID_THESAURUS.

## <a name="to-delete-an-entry-from-an-accelerator-table"></a>Chcete-li odstranit záznam z tabulky akcelerátorů

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte položku, kterou chcete odstranit. (Podržte stisknutou klávesu **Ctrl** nebo **Shift** klíče při výběru k výběru více položek.)

1. Klikněte pravým tlačítkem a zvolte **odstranit** v místní nabídce (nebo vyberte **odstranit** z **upravit** nabídky).

\- nebo –

- Stisknutím klávesy **odstranit** klíč.

## <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Přesunutí nebo kopírování záznamu tabulky akcelerátorů do jiného souboru skriptu prostředků

1. Otevřete v tabulkách akcelerátoru v obou souborů skriptu prostředků.

1. Vyberte položku, kterou chcete přesunout.

1. Z **upravit** nabídce zvolte **kopírování** nebo **Vyjmout**.

1. Vyberte položku v cílovém souboru skriptu prostředků.

1. Z **upravit** nabídce zvolte **vložit**.

   > [!NOTE]
   > Můžete také použít klávesové zkratky pro kopírování a vkládání.

## <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Změna vlastností vícenásobných kláves akcelerátoru

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte klávesy akcelerátoru chcete změnit tím, že se **Ctrl** klíče při výběru každé z nich.

1. Přejděte [okno vlastností](/visualstudio/ide/reference/properties-window) a zadejte hodnoty, které chcete všechny vybrané akcelerátorů sdílet.

   > [!NOTE]
   > Každá hodnota modifikátor se zobrazí jako vlastnost typu Boolean v **vlastnosti** okna. Pokud změníte [modifikátor](../windows/accelerator-modifier-property.md) hodnotu **vlastnosti** okně tabulky akcelerátorů považuje za new – modifikátor doplněk žádné modifikátory, které byly dříve. Proto pokud nastavíte všechny hodnoty modifikátor budete muset nastavit všechny z nich zajistit, že každý akcelerátor sdílí stejný **modifikátor** nastavení.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor akcelerátorů](../windows/accelerator-editor.md)<br/>
[Editory prostředků](../windows/resource-editors.md)
