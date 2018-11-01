---
title: Podpora kontextů aktivace ve stavu modulu MFC
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: c5e3d5c9195f18c54de63ec7ecd38b165feca5df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619019"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Podpora kontextů aktivace ve stavu modulu MFC

Knihovna MFC vytvoří aktivační kontext pomocí prostředku manifestu modulu pro uživatele k dispozici. Další informace o způsobu vytvoření kontextů aktivace naleznete v následujících tématech:

- [Kontexty aktivace](/windows/desktop/SbsCs/activation-contexts)

- [Manifesty aplikací](/windows/desktop/SbsCs/application-manifests)

- [Manifest sestavení](/windows/desktop/SbsCs/assembly-manifests)

## <a name="remarks"></a>Poznámky

Po přečtení těchto témat Windows SDK, mějte na paměti, že mechanismus MFC aktivační kontext se podobá aktivační kontext sady Windows SDK s tím rozdílem, že knihovny MFC nepoužívá rozhraní API Windows SDK aktivační kontext.

Aktivační kontext funguje v aplikacích MFC, knihovny DLL uživatele a rozšiřující knihovny DLL MFC následujícími způsoby:

- Aplikace MFC pomocí resource ID 1 pro jejich prostředku manifestu. V takovém případě MFC nevytváří své vlastní aktivační kontext, ale používá výchozí kontext aplikace.

- Uživatel MFC knihovny DLL pomocí resource ID 2 pro jejich prostředku manifestu. Knihovny MFC, vytvoří pro každou knihovnu DLL uživatelské aktivační kontext, takže jiný uživatel knihovny DLL můžete použít různé verze stejné knihovny (například knihovny běžných ovládacích prvků).

- Rozšiřující knihovny DLL MFC závisí na jejich hostitelské aplikace nebo uživatele knihovny DLL k navázání jejich aktivační kontext.

I když se stav aktivace kontextu může být upraveno pomocí postupů popsaných v části [pomocí rozhraní API místní aktivace](/windows/desktop/SbsCs/using-the-activation-context-api), použití mechanismu MFC aktivační kontext může být užitečné při vývoji na základě knihovnu DLL modulu plug-in architektury Pokud není jednoduché (nebo zcela znemožnit) Chcete-li ručně přepnout stav aktivace před a po jednotlivých volání externích modulů plug-in.

Aktivační kontext je vytvořen v [afxwininit –](../mfc/reference/application-information-and-management.md#afxwininit). Je zničen při `AFX_MODULE_STATE` destruktor. Popisovač kontextu k aktivaci se ukládají `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` je popsána v [afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate).)

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) – makro aktivuje a deaktivuje aktivační kontext. `AFX_MANAGE_STATE` je povolený pro statické knihovny MFC, knihovny DLL MFC, umožňující kódu knihovny MFC pro spuštění ve správné aktivační kontext zvolila DLL uživatele.

## <a name="see-also"></a>Viz také

[Kontexty aktivace](/windows/desktop/SbsCs/activation-contexts)<br/>
[Manifesty aplikací](/windows/desktop/SbsCs/application-manifests)<br/>
[Manifest sestavení](/windows/desktop/SbsCs/assembly-manifests)<br/>
[Afxwininit –](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[Afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)

