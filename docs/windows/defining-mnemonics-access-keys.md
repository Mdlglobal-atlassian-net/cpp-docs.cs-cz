---
title: Definice klávesových zkratek (přístupové klávesy) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls, mnemonics
- access keys [C++], checking
- mnemonics, checking for duplicate
- mnemonics
- mnemonics, dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a60cf597a88fcf7038848be6c9e2d31269f6a906
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873690"
---
# <a name="defining-mnemonics-access-keys"></a>Definice klávesových zkratek (přístupové klávesy)
Za normálních okolností klávesnice uživatelé Přesun zaměření pro vstup z jednoho ovládacího prvku do druhého v dialogovém okně s klíči KARTĚ a šipku. Však můžete definovat přístupový klíč (název klávesovými nebo snadno zapamatovat), který umožňuje uživatelům zvolit ovládacího prvku stisknutím jeden klíč.  
  
### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Chcete-li definovat přístupový klíč pro ovládací prvek s popiskem viditelné (tlačítek, zaškrtněte políčka a přepínače)  
  
1.  Vyberte ovládací prvek v dialogovém okně.  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window)v **popisek** vlastnost, zadejte nový název pro ovládací prvek, zadáním ampersand (**&**) před písmenem, který chcete používat jako přístupový klíč pro ovládací prvek. Například `&Radio1`.  
  
3.  Stiskněte klávesu **zadejte**.  
  
     Podtržení, které se zobrazí v zobrazení titulku udávajících přístupový klíč, například **R**adio1.  
  
### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Chcete-li definovat přístupový klíč pro ovládací prvek bez viditelné popisek  
  
1.  Proveďte popisek ovládacího prvku pomocí **statický Text** řídit ve [sada nástrojů](/visualstudio/ide/reference/toolbox).  
  
2.  Statický text titulku, zadejte znak ampersand (**&**) před písmenem, který chcete používat jako přístupový klíč.  
  
3.  Ujistěte se, že ovládacího prvku statický text okamžitě předchází řízení, které jsou označeny v pořadí.  
  
 Všechny klíče přístup v rámci dialogového okna musí být jedinečné.  
  
#### <a name="to-check-for-duplicate-access-keys"></a>Zkontrolujte duplicitní přístupové klávesy  
  
1.  Na **formátu** nabídky, klikněte na tlačítko **zkontrolovat klávesové zkratky**.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

