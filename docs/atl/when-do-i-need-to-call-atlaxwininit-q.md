---
title: Když je potřeba volat AtlAxWinInit? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinInit
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9aa1dd14ccae555d4ab9acbbac15e9b66cafe6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360270"
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>Když je potřeba volat AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) zaregistruje **"AtlAxWin80"** okno třídy (plus několik vlastní okno zpráv), tato funkce musí být volána, než se pokusíte vytvořit okno hostitele. Nicméně vždy nemusíte volání této funkce explicitně, od, který je hostitelem rozhraní API (a třídy, které je používají) pro vás často volání této funkce. Neexistuje žádné škodu při volání této funkce více než jednou. .  
  
## <a name="see-also"></a>Viz také  
 Když je potřeba volat AtlAxWinTerm     
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)
