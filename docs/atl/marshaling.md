---
title: "Zařazování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ec8c85606f0f0ef3de67a61181ead6537fde179e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="marshaling"></a>Zařazování
Technika COM zařazování umožňuje rozhraní vystavené objekt v jednom procesu, který se má použít v jiném procesu. V kódování, COM poskytuje kód (nebo kód poskytl uživatel provádějící implementaci rozhraní používá) do pack parametry metody do formátu, který lze přesunout mezi procesy (i v drátové síti pro procesy spuštěné na jiné počítače) a rozbalte tyto parametry na druhém konci. COM, musíte provést stejný postup pro návrat z volání.  
  
> [!NOTE]
>  Zařazování není obvykle nutné při rozhraní poskytované objekt se používá v rámci jednoho procesu jako objekt. Zařazování však může být potřeba mezi vlákny.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [Zařazování podrobnosti](http://msdn.microsoft.com/library/windows/desktop/ms692621)
