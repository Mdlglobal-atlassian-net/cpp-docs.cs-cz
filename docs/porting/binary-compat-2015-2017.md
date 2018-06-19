---
title: C++ binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2017 | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcd315631d74c652177dba99cbe533ad91f68474
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33838979"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>C++ binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2017


V předchozích verzích sady Visual Studio binární kompatibilitu mezi soubory objektů (OBJs), statické knihovny (knihovny), dynamické knihovny (DLL) a vytvořené s použitím různých verzích nástrojů a modulu runtime knihoven kompilátoru spustitelné soubory (souborů exe) nebyla zaručit. To se změnilo v Visual Studio 2017. V sadě Visual Studio 2015 a Visual Studio 2017 hlavní číslo nástrojů C++ je 14 (v140 pro sadu Visual Studio 2015 a v141 pro Visual Studio 2017). Tento údaj zohledňuje skutečnost, že do modulu runtime knihoven a aplikace, kompilovat s jakoukoli verzí kompilátoru jsou – pro nejvíce část – binární kompatibilní. To znamená, například můžete vytvořit knihovny DLL ve Visual Studio 2017 a využívat z aplikace, kompilovat s Visual Studio 2015 nebo pomocí aplikace vytvořené pomocí sady nástrojů 2015 redistributable knihovny Visual Studio 2017.  

Existují dvě výjimky pro toto pravidlo. Binární kompatibilita není zaručena v těchto případech:  

1) Když jsou statické knihovny nebo soubory objektů kompilovat s přepínače kompilátoru /GL.  

2) Při využívání knihovny sestaven pomocí nástrojů, jehož verze je vyšší než sady nástrojů, které používají ke kompilaci a odkaz aplikaci. Například program, který je zkompilovat a propojit s nástrojů 19.12 spotřebovat knihovny, které jsou kompilovat s 19.0 až prostřednictvím 19.12. Propojování 19.x programy s knihovnami vyprodukované Visual Studio 2013 nebo starší není podporována.


## <a name="see-also"></a>Viz také  

[Historie změn Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)


