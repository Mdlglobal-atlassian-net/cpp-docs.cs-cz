---
title: 'Postupy: Přidání podpory MFC do souborů skriptu prostředků | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85f4930e1d0a84091686729bacccf6a62977de6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608080"
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Postupy: Přidání podpory MFC do souborů skriptu prostředků

Za normálních okolností při sestavení aplikace knihovny MFC pro používání Windows [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), průvodce vygeneruje základní sadu souborů (včetně souboru prostředků skriptů (.rc)), který obsahuje základní funkce Microsoft Foundation třídy (MFC). Nicméně pokud upravujete soubor .rc pro aplikaci Windows, která není založena na knihovně MFC, následující funkce specifické pro rozhraní knihovny MFC nejsou k dispozici:

- Průvodci kódem knihovny MFC (dříve označované jako "[MFC ClassWizard](http://msdn.microsoft.com/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")

- Řetězce výzev nabídky

- Obsah seznamu pro pole se seznamem

- Hostování ovládacího prvku ActiveX

Můžete však přidat podporu knihovny MFC do existujících .rc souborů, které ji nemají.

### <a name="to-add-mfc-support-to-rc-files"></a>Přidání podpory MFC do souborů .rc

1. Otevření souboru skriptu prostředků.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V [zobrazení prostředků](../windows/resource-view-window.md), zvýrazněte složku prostředků (například MFC.rc).

3. V [okno vlastností](/visualstudio/ide/reference/properties-window), nastavte **MFC režimu** vlastnost **True**.

   > [!NOTE]
   > Kromě nastavení tohoto příznaku soubor .rc musí být součástí projektu knihovny MFC. Například pouhé nastavení **MFC režimu** k **True** na souboru .rc v Win32 projektu vám neposkytne žádné funkce knihovny MFC.

## <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)