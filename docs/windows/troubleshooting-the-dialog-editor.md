---
title: Řešení potíží s editorem dialogového okna (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 21882868-5ac4-4a41-a4a6-eaaa059402ea
ms.openlocfilehash: fe0fe704b5c17d0db4e3419f29d21f0e60bc4211
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484952"
---
# <a name="troubleshooting-the-dialog-editor-c"></a>Řešení potíží s editorem dialogového okna (C++)

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

Níže jsou uvedeny několik problémů, které byste měli vědět při práci v C++ **dialogové okno** editoru:

## <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Přidání ovládacích prvků do dialogového okna způsobí, že dialog už – funkce

Po přidání běžného ovládacího prvku nebo ovládací prvek RTF do dialogového okna, nebude se zobrazovat při testování dialogových oken nebo dialogového okna, samotné se nezobrazí.

### <a name="example-of-the-problem"></a>Příklad problému

1. Vytvořte projekt Win32, změna nastavení aplikace, proto vytvořit aplikace Windows (ne konzolovou aplikaci).

1. V [zobrazení prostředků](../windows/resource-view-window.md), dvakrát klikněte na soubor .rc.

1. V části Možnosti dialogového okna, dvakrát klikněte **o** pole.

1. Přidat **ovládací prvek adresy IP** do dialogového okna.

1. Uložit a **sestavit vše znovu**.

1. Spuštění programu.

1. V dialogových oken **pomáhají** nabídky, klikněte na tlačítko **o** příkaz; žádné dialogové okno zobrazí okno.

### <a name="the-cause"></a>Příčinu

V současné době **dialogové okno** editor nepřidává automaticky kódu do projektu při přetažení následující běžné ovládací prvky nebo ovládací prvky na dialogové okno pro úpravy s formátováním. Ani sada Visual Studio poskytuje chybu nebo upozornění při výskytu tohoto problému. Pokud chcete vyřešit, přidejte kód pro ovládací prvek ručně.

||||
|-|-|-|
|Ovládací prvek posuvníku|Ovládací prvek stromu|Výběr data a času|
|Ovládací prvek typu číselník|Ovládací prvek karty|Měsíční kalendář|
|Ovládací prvek průběh|Animace ovládacího prvku|Ovládací prvek adresy IP|
|Klávesová zkratka|Ovládací prvek pro úpravy s formátováním|Rozšířené pole se seznamem|
|Ovládací prvek seznamu|Ovládací prvek pro úpravy s formátováním 2.0|Vlastní ovládací prvek|

### <a name="fix-for-common-controls"></a>Oprava pro běžné ovládací prvky

Použití běžných ovládacích prvků v dialogovém okně, je třeba volat [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) nebo `AFXInitCommonControls` předtím, než vytvoříte dialogové okno.

### <a name="fix-for-richedit-controls"></a>Oprava pro ovládací prvky RichEdit

Je nutné volat `LoadLibrary` pro ovládací prvky pro úpravy s formátováním. Další informace najdete v tématu [o bohaté upravit ovládací prvky](/windows/desktop/Controls/about-rich-edit-controls) v sadě Windows SDK a [– Přehled ovládacího prvku Rich upravit](../mfc/overview-of-the-rich-edit-control.md).

### <a name="requirements"></a>Požadavky

Win32

## <a name="using-the-richedit-10-control-with-mfc"></a>Použití ovládacího prvku RichEdit 1.0 s MFC

Použití ovládacího prvku RichEdit, nejprve je třeba volat [afxinitrichedit2 –](../mfc/reference/application-information-and-management.md#afxinitrichedit2) načíst ovládacího prvku RichEdit 2.0 (RICHED20. Knihovny DLL), nebo se telefonicky [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) načíst starší ovládacího prvku RichEdit 1.0 (RICHED32. KNIHOVNY DLL).

Můžete použít aktuální [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) třída s atributem starší ovládacího prvku RichEdit 1.0, ale `CRichEditCtrl` je určen pouze pro podporu ovládacího prvku RichEdit 2.0. Protože jsou podobné RichEdit 1.0 a RichEdit 2.0, většina metod bude fungovat. Mějte však na paměti, že existují určité rozdíly mezi 1.0 nebo 2.0 ovládací prvky, takže mohou některé metody nebudou správně fungovat nebo nepracuje vůbec.

### <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Editor dialogových oken](../windows/dialog-editor.md)