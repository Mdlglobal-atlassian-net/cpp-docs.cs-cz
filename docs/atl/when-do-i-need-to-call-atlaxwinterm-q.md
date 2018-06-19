---
title: Když je potřeba volat AtlAxWinTerm? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinTerm
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61830023d3fb67d331784769f32cda4eee8355b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360159"
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>Když je potřeba volat AtlAxWinTerm?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) zrušení registrace **"AtlAxWin80"** třídy oken. Tato funkce by měly volat (pokud už je potřeba vytvořit hostitele windows), po všechny existující hostitele windows zničena. Pokud nemáte volání této funkce, třída okno bude zrušena automaticky při ukončení procesu.  
  
## <a name="see-also"></a>Viz také  
 Když je potřeba volat AtlAxWinInit  
[Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

