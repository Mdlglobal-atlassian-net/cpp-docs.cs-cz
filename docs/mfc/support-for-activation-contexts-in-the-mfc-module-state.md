---
title: Podpora kontextů aktivace ve stavu modulu MFC
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: 296df3d2ecec74c5c9a7deef1617298d40243724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511431"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Podpora kontextů aktivace ve stavu modulu MFC

Knihovna MFC vytvoří aktivační kontext pomocí prostředku manifestu poskytnutého modulem uživatele. Další informace o tom, jak jsou kontexty aktivace vytvořeny, najdete v následujících tématech:

- [Kontexty aktivace](/windows/win32/SbsCs/activation-contexts)

- [Manifesty aplikace](/windows/win32/SbsCs/application-manifests)

- [Manifesty sestavení](/windows/win32/SbsCs/assembly-manifests)

## <a name="remarks"></a>Poznámky

Při čtení těchto Windows SDKch témat si všimněte, že mechanismus aktivačního kontextu technologie MFC připomíná kontext aktivace Windows SDK s tím rozdílem, že knihovna MFC nepoužívá rozhraní API kontextu aktivace Windows SDK.

Aktivační kontext funguje v aplikacích knihovny MFC, uživatelských knihoven DLL a knihovnách DLL rozšíření MFC následujícími způsoby:

- Aplikace MFC používají pro svůj prostředek manifestu ID prostředku 1. V tomto případě knihovna MFC nevytvoří svůj vlastní kontext aktivace, ale používá výchozí kontext aplikace.

- Knihovny DLL uživatelů knihovny MFC používají pro svůj prostředek manifestu ID prostředku 2. V tomto případě knihovna MFC vytvoří kontext aktivace pro každou uživatelskou knihovnu DLL, takže různé knihovny DLL uživatelů mohou používat různé verze stejných knihoven (například knihovny běžných ovládacích prvků).

- Knihovny DLL rozšíření MFC využívají své hostující aplikace nebo uživatelské knihovny DLL k vytvoření svého aktivačního kontextu.

I když lze stav kontextu aktivace upravit pomocí procesů popsaných v části [použití rozhraní API kontextu aktivace](/windows/win32/SbsCs/using-the-activation-context-api), může být použití mechanismu aktivačního kontextu knihovny MFC užitečné při vývoji architektury modulu plug-in založeného na knihovně DLL, kde není jednoduché (nebo není možné) Ruční přepnutí stavu aktivace před a po jednotlivých voláních externích modulů plug-in.

Aktivační kontext je vytvořen v [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit). Je zničen v `AFX_MODULE_STATE` destruktoru. Popisovač aktivačního kontextu je uložen v `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` je popsáno v [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate).)

Makro [volají](reference/extension-dll-macros.md#afx_manage_state) aktivuje a deaktivuje aktivační kontext. `AFX_MANAGE_STATE`je povolen pro statické knihovny MFC a také knihovny MFC DLL, aby bylo možné spustit kód knihovny MFC ve správném aktivačním kontextu vybraném pomocí knihovny DLL uživatele.

## <a name="see-also"></a>Viz také:

[Kontexty aktivace](/windows/win32/SbsCs/activation-contexts)<br/>
[Manifesty aplikace](/windows/win32/SbsCs/application-manifests)<br/>
[Manifesty sestavení](/windows/win32/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
