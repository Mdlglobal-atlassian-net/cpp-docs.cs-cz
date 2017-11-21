---
title: "Základní třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 200dc2a4bb53365c15457f016ac391bb48d4c278
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="base-classes"></a>Třídy Base
Proces dědičnosti vytvoří novou odvozenou třídu, která je tvořena členy základní třídy a všemi novými členy přidanými touto odvozenou třídou. Ve vícenásobné dědičnosti je možné sestrojit graf dědičnosti, kde je stejná základní třída součástí více než jedné z odvozených tříd. Následující obrázek znázorňuje takový graf.  
  
 ![Více instancí základní třídy](../cpp/media/vc38xn1.gif "vc38XN1")  
Více instancí jediné základní třídy  
  
 Na obrázku jsou zobrazena vyobrazení komponent `CollectibleString` a `CollectibleSortable`. Avšak základní třída `Collectible` je v třídě `CollectibleSortableString` použita s použitím cesty `CollectibleString` a cesty `CollectibleSortable`. Chcete-li tuto redundanci odstranit, mohou být tyto třídy deklarovány jako virtuální základní třídy, když jsou zděděny.  
  
