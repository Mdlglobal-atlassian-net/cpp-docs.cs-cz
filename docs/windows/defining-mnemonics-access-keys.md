---
title: Definice klávesových zkratek (přístupové klávesy)
ms.date: 11/04/2016
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: 8682ab38abebe1c453ef562e8eaac0e627f5c4bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488917"
---
# <a name="defining-mnemonics-access-keys"></a>Definice klávesových zkratek (přístupové klávesy)

Za normálních okolností uživatelé klávesnice Přesun zaměření pro vstup z jednoho ovládacího prvku do druhého v dialogovém okně s **kartu** a **šipku** klíče. Ale můžete definovat přístupovou klávesu (název mnemonická nebo snadno zapamatovat), který umožňuje uživatelům vybrat ovládací prvek stisknutím klávesy jeden klíč.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Chcete-li definovat přístupovou klávesu pro ovládací prvek titulkem viditelné (tlačítka, zaškrtávací políčka a přepínačů)

1. Vyberte ovládací prvek v dialogovém okně.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window)v **titulek** vlastnost, zadejte nový název pro ovládací prvek psaní znak ampersand (`&`) před písmeno jako přístupový klíč pro tento ovládací prvek. Například `&Radio1`.

3. Stisknutím klávesy **zadejte**.

   Podtržení se zobrazí v zobrazení titulku udávajících přístupový klíč, například **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Chcete-li definovat přístupovou klávesu pro ovládací prvek bez zobrazen titulek

1. Provádění dotazů pomocí popisek pro ovládací prvek **statický Text** v ovládacím prvku [nástrojů](/visualstudio/ide/reference/toolbox).

2. Statický text titulku, zadejte znak ampersand (`&`) před písmeno jako přístupový klíč.

3. Ujistěte se, že ovládací prvek statického textu bezprostředně předchází ovládací prvek, který ho popisky v pořadí.

Přístupové klíče v rámci dialogového okna musí být jedinečné.

### <a name="to-check-for-duplicate-access-keys"></a>Hledat duplicitní přístupové klávesy

1. Na **formátu** nabídky, klikněte na tlačítko **zkontrolujte klávesových zkratek**.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)