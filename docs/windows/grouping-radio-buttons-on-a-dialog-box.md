---
title: Seskupení přepínačů v dialogovém okně | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.grouping
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls, grouping radio buttons
- grouping controls
- radio buttons, grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d0846d87273920f72598a1ea5bc4bd83d4c952d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599882"
---
# <a name="grouping-radio-buttons-on-a-dialog-box"></a>Seskupení přepínačů v dialogovém okně

Při přidání přepínacích tlačítek do dialogového okna s nimi zacházet jako se skupinou tak, že nastavíte **skupiny** vlastnost **vlastnosti** okno pro první tlačítka ve skupině. ID ovládacího prvku pro tento přepínač se pak objeví v [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), abyste mohli přidat členskou proměnnou pro skupinu přepínačů.

Můžete mít více než jedné skupině přepínačů v dialogovém okně a každá skupina by se měl přidat pomocí následujícího postupu.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Do dialogového okna Přidat skupinu přepínačů

1. Vyberte ovládací prvek přepínač tlačítko v [okno nástrojů](/visualstudio/ide/reference/toolbox) a klikněte na umístění v dialogovém okně místo, kam chcete umístit ovládací prvek.

2. Zopakujte krok 1 pro přidání tolika přepínačů, podle potřeby. Ujistěte se, že přepínací tlačítka ve skupině jsou po sobě jdoucích v pořadí (Další informace najdete v tématu [Změna pořadí karty ovládací prvky](../windows/changing-the-tab-order-of-controls.md)).

3. V [okno vlastností](/visualstudio/ide/reference/properties-window), nastavte **skupiny** vlastnost *první* přepínač v pořadí karet na **True**.

   Změna **skupiny** vlastnost **True** přidá WS_GROUP styl tlačítka položky v objektu dialogového okna skriptu, prostředků a zajistí, že uživatel zvolit pouze jeden přepínací tlačítko současně na tlačítku skupiny (když uživatel klikne jeden přepínací tlačítko, ostatní ve skupině jsou vymazány).

   > [!NOTE]
   > Pouze první přepínací tlačítko ve skupině by měly mít **skupiny** vlastnost nastavena na hodnotu **True**. Pokud máte další ovládací prvky, které nejsou součástí skupiny tlačítko, nastavte **skupiny** vlastnost první ovládací prvek *, která je mimo skupinu* k **True** také. Můžete rychle identifikovat první ovládací prvek mimo skupinu stisknutím kombinace kláves **Ctrl**+**D** Chcete-li zobrazit pořadí ovládacích prvků.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Přidání členské proměnné pro skupina přepínacích tlačítek

1. Klikněte pravým tlačítkem na první tlačítko ovládacím prvku přepínač v pořadí (dominantního ovládacího prvku a ten se **skupiny** nastavenou na hodnotu True).

2. Zvolte **přidat proměnnou** z místní nabídky.

3. V [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), vyberte **řídicí proměnná** zaškrtněte políčko a potom vyberte **hodnotu** přepínač.

4. V **název proměnné** zadejte název pro novou proměnnou člena.

5. V **typ proměnné** pole se seznamem, vyberte **int** nebo typ `int`.

6. Nyní můžete upravit kódu k určení, jaké tlačítko přepínače by se měla zobrazit vybraný. Například `m_radioBox1 = 0;` vybere první přepínací tlačítko ve skupině.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)  
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
[Ovládací prvky](../mfc/controls-mfc.md)