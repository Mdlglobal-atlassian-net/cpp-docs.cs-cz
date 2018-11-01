---
title: 'Postupy: Přidání podpory MFC do souborů skriptu prostředků (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.add.MFC
helpviewer_keywords:
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
ms.openlocfilehash: c2d0f9ee30085bd2bcc02cf48fd18f6de63eb69a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594386"
---
# <a name="how-to-add-mfc-support-to-resource-script-files-c"></a>Postupy: Přidání podpory MFC do souborů skriptu prostředků (C++)

Za normálních okolností při sestavení aplikace knihovny MFC pro používání Windows [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), průvodce vygeneruje základní sadu souborů (včetně souboru prostředků skriptů (.rc)), který obsahuje základní funkce Microsoft Foundation třídy (MFC). Nicméně pokud upravujete soubor .rc pro aplikaci Windows, která není založena na knihovně MFC, následující funkce specifické pro rozhraní knihovny MFC nejsou k dispozici:

- Průvodci kódem knihovny MFC

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

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)