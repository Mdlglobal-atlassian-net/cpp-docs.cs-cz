---
title: "Izolace MFC běžné ovládací prvky knihovny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: effc8b927aadc821e189837ab3506f05cb426e93
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Izolace knihovny běžných ovládacích prvků MFC
Běžné ovládací prvky knihovny je nyní izolovaná v rámci MFC, což jiné moduly (například uživatel knihovny DLL) do zadáním verze v jejich manifesty používají různé verze knihovny běžných ovládacích prvků.  
  
 Aplikace MFC (nebo uživatelský kód volá MFC) volá rozhraní API prostřednictvím funkce obálky s názvem knihovnu běžných ovládacích prvků `Afx` *%{FunctionName/*, kde *%{FunctionName/* je název běžné Ovládací prvky rozhraní API. Tyto funkce obálky jsou definovány v afxcomctl32.h a afxcomctl32.inl.  
  
 Můžete použít [afx_comctl32_if_exists –](reference/run-time-object-model-services.md#afx_comctl32_if_exists) a [afx_comctl32_if_exists2 –](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) makra (definovaná v afxcomctl32.h) k určení, zda knihovny běžných ovládacích prvků implementuje určité API místo volání [GetProcAddress](../build/getprocaddress.md).  
  
 Technicky je volat běžné ovládací prvky knihovny rozhraní API prostřednictvím obálkovou třídu, `CComCtlWrapper` (definovanou v afxcomctl32.h). `CComCtlWrapper`je také zodpovědná za načítání a uvolňování souboru Comctl32.dll. Stavu modulu MFC obsahuje ukazatel na instanci `CComCtlWrapper`. Můžete přistupovat pomocí třídy obálku `afxComCtlWrapper` makro.  
  
 Všimněte si, že volání rozhraní API přímo běžné ovládací prvky (není pomocí funkce MFC obálky) z knihovny MFC aplikaci nebo uživatele DLL bude fungovat ve většině případů, protože aplikace knihovny MFC nebo uživatelské knihovny DLL je vázána na vyžádání v manifestu knihovny běžných ovládacích prvků). Samotný kód MFC má však používat obálky, protože MFC kód může být volána z knihoven DLL uživatele s různými verzemi knihovny běžných ovládacích prvků.

