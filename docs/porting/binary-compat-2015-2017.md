---
title: "C++ binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2017 | Microsoft Docs"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89bb772976050c8ebf0b7745aa0541c2de3e2fed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>C++ binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2017


V předchozích verzích sady Visual Studio binární kompatibilitu mezi soubory objektů (OBJs), statické knihovny (knihovny), dynamické knihovny (DLL) a vytvořené s použitím různých verzích nástrojů a modulu runtime knihoven kompilátoru spustitelné soubory (souborů exe) nebyla zaručit. To se změnilo v Visual Studio 2017. V sadě Visual Studio 2015 a Visual Studio 2017 hlavní číslo nástrojů C++ je 14 (v140 pro sadu Visual Studio 2015 a v141 pro Visual Studio 2017). Tento údaj zohledňuje skutečnost, že do modulu runtime knihoven a aplikace, kompilovat s jakoukoli verzí kompilátoru jsou – pro nejvíce část – binární kompatibilní. To znamená, například můžete vytvořit knihovny DLL ve Visual Studio 2017 a využívat z aplikace, kompilovat s Visual Studio 2015 nebo pomocí aplikace vytvořené pomocí sady nástrojů 2015 redistributable knihovny Visual Studio 2017.  

Existují dvě výjimky pro toto pravidlo. Binární kompatibilita není zaručena v těchto případech:  

1) Když jsou statické knihovny nebo soubory objektů kompilovat s přepínače kompilátoru /GL.  

2) Pokud aplikace využívá redistributable knihovny, jejichž číslo verze je menší než sady nástrojů, který se používá ke kompilaci aplikace. Jinými slovy pokud zkompilujete program s v141 sada nástrojů platformy, všechny redistributable knihovny, které využívá aplikace musí být kompilované s v141 nebo vyšší.  

## <a name="see-also"></a>Viz také  

[Historie změn Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)


