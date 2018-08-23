---
title: Úprava řetězce v prostředku informací o verzi | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ec71759deabfa1b5ff7337befa85bdd9c492ae9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607498"
---
# <a name="editing-a-string-in-a-version-information-resource"></a>Úprava řetězce v prostředku informací o verzi

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Úprava řetězce v prostředku informací o verzi

1. Vyberte, pak znovu zahajte úprav klikněte na položku jednou. Provést změny přímo ve **informace o verzi** tabulky nebo [okno vlastností](/visualstudio/ide/reference/properties-window). Provedené změny se projeví na obou místech.

   > [!NOTE] 
   > Při úpravě `FILEFLAGS` klíče v **informace o verzi** editoru, můžete si všimnout nelze nastavit **ladění**, **soukromého sestavení**, nebo **speciální Sestavení** vlastnosti (v **vlastnosti** okno) pro soubory .rc:

   - **Informace o verzi** editor sad **ladění** vlastnost s `#ifdef` ve skriptu prostředků na základě `_DEBUG` sestavení příznak.

   - Pokud `Private Build` klíč má **hodnotu** nastavit **informace o verzi** tabulce, odpovídající **soukromého sestavení** vlastnost (v **vlastnosti**  okno) pro `FILEFLAGS` klíč bude **True**. Pokud **hodnotu** je prázdné, bude vlastnost **False**. Podobně **speciální sestavení** klíč (v **informace o verzi** tabulky) se váže na **speciální sestavení** vlastnost `FILEFLAGS` klíč.

Informace o pořadí bloku řetězec lze seřadit klepnutím na klíč, nebo hodnota záhlaví sloupců. Tyto položky automaticky uspořádat informace do zvolené sekvenci.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor informací o verzi](../windows/version-information-editor.md)  
[Informace o verzi (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)