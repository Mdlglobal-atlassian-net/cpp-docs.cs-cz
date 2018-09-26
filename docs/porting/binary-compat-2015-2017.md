---
title: Binární kompatibilita C++ Visual Studio 2015 a Visual Studio 2017 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/24/2018
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
ms.openlocfilehash: 4cedef2d5343b93c544ab22c41d2e5ac661bc3dd
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169564"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Binární kompatibilita C++ Visual Studio 2015 a Visual Studio 2017

V předchozích verzích sady Visual Studio binární kompatibilitu mezi soubory objektů (OBJs), statické knihovny (knihovny), dynamické knihovny (DLL) a spustitelných souborů (exe) vytvořené pomocí jiných verzí kompilátoru sadu nástrojů a modulu runtime knihoven nebyl zaručená. To byl změněn v sadě Visual Studio 2017. Hlavní číslo sady nástrojů C++ v sadě Visual Studio 2015 a Visual Studio 2017, je 14 (v140 pro Visual Studio 2015 a v141 pro Visual Studio 2017). To odpovídá skutečnost, že modul runtime knihovny a aplikace kompilované s jakoukoli verzí kompilátoru jsou--pro největší část--binární kompatibilní. To znamená například, že pokud máte knihovnu DLL v sadě Visual Studio 2015, není nutné znovu zkompilovat aby bylo možné využívat z aplikace, která je integrovaná se sadou Visual Studio 2017.  

Existují dvě výjimky z tohoto pravidla. Binární kompatibilita není zaručena v těchto případech:  

1. Když zkompilovaná statických knihoven nebo objektových souborů `/GL` přepínač kompilátoru.  

2. Při využívání knihovny vytvořené pomocí nástrojů, jehož verze je větší než sada nástrojů používá ke kompilaci a odkaz aplikaci. Například program, který je zkompilován a propojit s verzí kompilátoru 19.12 může spotřebovat knihovny, které jsou kompilovány pomocí verzi 19.0 nahoru prostřednictvím 19.12. Navíc binární kompatibilitu existuje pouze mezi Visual Studio 2015 a Visual Studio 2017; nepodporuje propojování programů 19.x s knihovnami Visual Studio 2013 nebo starší.

## <a name="see-also"></a>Viz také  

[Historie změn Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)
