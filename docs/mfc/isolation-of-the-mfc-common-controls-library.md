---
title: Izolace knihovny MFC běžné ovládací prvky knihovny | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3189b2e3db594801fe417ca43867da7db2e18fd7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423777"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Izolace knihovny běžných ovládacích prvků MFC

Knihovny běžných ovládacích prvků nyní izolované v knihovně MFC, což různých modulů (jako je například uživatel knihovny DLL) pro používají různé verze knihovny běžných ovládacích prvků tak, že zadáte verze ve svých manifestech.

Aplikace MFC (nebo uživatelský kód, volá se v prostředí MFC) provede volání do rozhraní API prostřednictvím funkce obálky s názvem knihovny běžných ovládacích prvků `Afx` *FunctionName*, kde *FunctionName* je běžný název Ovládací prvky rozhraní API. Tyto funkce obálky jsou definovány v afxcomctl32.h a afxcomctl32.inl.

Můžete použít [AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists) a [AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) makra (definovaná v afxcomctl32.h) k určení, zda knihovny běžných ovládacích prvků implementuje určitých rozhraní API namísto volání metody [GetProcAddress](../build/getprocaddress.md).

Technicky vzato provádět volání do rozhraní API pro běžné ovládací prvky knihovny prostřednictvím obálkovou třídu `CComCtlWrapper` (definováno v afxcomctl32.h). `CComCtlWrapper` je také zodpovědná za načítání a uvolňování souboru Comctl32.dll. Stavu modulu MFC obsahuje ukazatel na instanci `CComCtlWrapper`. Můžete přistupovat pomocí třídy obálky `afxComCtlWrapper` – makro.

Všimněte si, že volání rozhraní API přímo běžných ovládacích prvků (bez použití MFC – funkce obálky) z knihovny MFC aplikaci nebo uživatele knihovny DLL bude fungovat ve většině případů, protože aplikace knihovny MFC nebo uživatelské knihovny DLL je vázán na knihovny běžných ovládacích prvků požadovaný v jeho manifestu). Samotný kód knihovny MFC má však použít obálky, protože kód knihovny MFC může být volána z knihovny DLL uživatele s různými verzemi knihovny běžných ovládacích prvků.

