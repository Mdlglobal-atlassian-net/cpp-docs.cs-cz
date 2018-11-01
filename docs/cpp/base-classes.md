---
title: Třídy Base
ms.date: 11/04/2016
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
ms.openlocfilehash: faae9ba8591f296a48665e481678e2808aae7662
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628297"
---
# <a name="base-classes"></a>Třídy Base

Proces dědičnosti vytvoří novou odvozenou třídu, která je tvořena členy základní třídy a všemi novými členy přidanými touto odvozenou třídou. Ve vícenásobné dědičnosti je možné sestrojit graf dědičnosti, kde je stejná základní třída součástí více než jedné z odvozených tříd. Následující obrázek znázorňuje takový graf.

![Více instancí základní třídy](../cpp/media/vc38xn1.gif "vc38XN1") více instancí jediné základní třídy

Na obrázku jsou zobrazena vyobrazení komponent `CollectibleString` a `CollectibleSortable`. Avšak základní třída `Collectible` je v třídě `CollectibleSortableString` použita s použitím cesty `CollectibleString` a cesty `CollectibleSortable`. Chcete-li tuto redundanci odstranit, mohou být tyto třídy deklarovány jako virtuální základní třídy, když jsou zděděny.