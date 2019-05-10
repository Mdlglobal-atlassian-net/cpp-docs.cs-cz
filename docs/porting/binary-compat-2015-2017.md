---
title: C++Binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2019
ms.date: 05/03/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 052874eb9273ee9a9ce1695ffdadedd9911673e1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449052"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++Binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2019

V sadě Visual Studio 2013 a starší není zaručeno, že binární kompatibilitu mezi soubory objektů (OBJs), statické knihovny (knihovny), dynamické knihovny (DLL) a spustitelných souborů (exe) vytvořené pomocí jiných verzí kompilátoru sadu nástrojů a modulu runtime knihoven. 

V sadě Visual Studio 2015 a novější C++ nástrojů hlavní číslo je 14 (v140 pro Visual Studio 2015, Visual Studio 2017 v141 a v142 pro Visual Studio 2019). To odpovídá vzhledem k tomu, že modul runtime knihovny a aplikace kompilované s jakoukoli verzí kompilátoru mají binární kompatibilní. To znamená, že pokud máte knihovny třetí strany, který byl vytvořen pomocí sady Visual Studio 2015, není nutné znovu zkompilovat aby bylo možné využívat z aplikace sestavené aplikací Visual Studio 2017 nebo Visual Studio 2019.

Jedinou výjimkou tohoto pravidla je, že statické knihovny nebo objektové soubory, které jsou kompilovány pomocí `/GL` přepínač kompilátoru nejsou kompatibilní s binární. 

Když kombinovat binární soubory sestavené pomocí různých podporované verze sady nástrojů MSVC, vizuál C++ zabere redistributable, spustí se vaše aplikace nemůže být starší než verze nástrojů sloužící k sestavení aplikace nebo všechny knihovny. 

## <a name="see-also"></a>Viz také:

[Historie změn Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
