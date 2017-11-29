---
title: "Když je potřeba volat AtlAxWinInit? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinInit
dev_langs: C++
helpviewer_keywords: AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ec7d8d15b8219071b593368ed539d92ff3c9032
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>Když je potřeba volat AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) zaregistruje **"AtlAxWin80"** okno třídy (plus několik vlastní okno zpráv), tato funkce musí být volána, než se pokusíte vytvořit okno hostitele. Nicméně vždy nemusíte volání této funkce explicitně, od, který je hostitelem rozhraní API (a třídy, které je používají) pro vás často volání této funkce. Neexistuje žádné škodu při volání této funkce více než jednou. .  
  
## <a name="see-also"></a>Viz také  
 Když je potřeba volat AtlAxWinTerm     
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)