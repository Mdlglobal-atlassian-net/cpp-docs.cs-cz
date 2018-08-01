---
title: Základní třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1375cee34266b8d751e9c8d88fb22ce56f6c044
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407985"
---
# <a name="base-classes"></a>Třídy Base
Proces dědičnosti vytvoří novou odvozenou třídu, která je tvořena členy základní třídy a všemi novými členy přidanými touto odvozenou třídou. Ve vícenásobné dědičnosti je možné sestrojit graf dědičnosti, kde je stejná základní třída součástí více než jedné z odvozených tříd. Následující obrázek znázorňuje takový graf.  
  
 ![Více instancí základní třídy](../cpp/media/vc38xn1.gif "vc38XN1")  
Více instancí jediné základní třídy  
  
 Na obrázku jsou zobrazena vyobrazení komponent `CollectibleString` a `CollectibleSortable`. Avšak základní třída `Collectible` je v třídě `CollectibleSortableString` použita s použitím cesty `CollectibleString` a cesty `CollectibleSortable`. Chcete-li tuto redundanci odstranit, mohou být tyto třídy deklarovány jako virtuální základní třídy, když jsou zděděny.  