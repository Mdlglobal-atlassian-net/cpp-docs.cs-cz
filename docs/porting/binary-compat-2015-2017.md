---
title: C++binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019
description: Popisuje způsob fungování binární kompatibility mezi kompilovanými C++ soubory v sadě Visual Studio 2015, 2017 a 2019. Jeden balíček Microsoft C++ Visual Redistributable Package funguje pro všechny tři verze.
ms.date: 11/07/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: e41c34abe25deefe100f525044faeac0b0c3054a
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912876"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019

V Microsoft Visual Studio 2013 a starších verzích není binární kompatibilita zaručená mezi soubory objektů (OBJs), statickými knihovnami (knihovny), knihovnami DLL (Dynamic-Link Library) a spustitelnými soubory (exe), které byly sestaveny pomocí různých verzí sady nástrojů kompilátoru. a běhové knihovny.

V sadě Visual Studio 2015 nebo novější je C++ hlavní číslo sady nástrojů 14 (V140 for visual Studio 2015, V141 for visual Studio 2017 a V142 for visual Studio 2019). Toto číslování odráží skutečnost, že běhové knihovny i aplikace zkompilované pomocí kterékoli z těchto verzí kompilátoru jsou binární kompatibilní. Proto pokud máte knihovnu třetí strany, která byla sestavena se sadou Visual Studio 2015, nemusíte ji znovu kompilovat, aby ji bylo možné využívat z aplikace vytvořené pomocí sady Visual Studio 2017 nebo Visual Studio 2019.

Jedinou výjimkou z tohoto pravidla je, že statické knihovny nebo soubory objektů, které jsou kompilovány s přepínačem `/GL` *kompilátoru, nejsou binární kompatibilní* .

Při smíchání binárních souborů sestavených s různými podporovanými verzemi sady C++ nástrojů Microsoft (MSVC) sada Visual C++ Redistributable Package, na které vaše aplikace běží, nemůže být starší než kterákoli z verzí sady nástrojů, která se používá k sestavení vaší aplikace nebo všech knihoven, které spotřebovává.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Upgrade Microsoft Visual C++ Redistributable ze sady visual Studio 2015 nebo 2017 na visual Studio 2019

Vzhledem k tomu, že jsme zachovali binární kompatibilitu a zachovali hlavní verzi (14) v rámci C++ Microsoft Visual Redistributable pro visual Studio 2015, 2017 a 2019, můžete z nich kdykoli nainstalovat jenom C++ jednu verzi sady Visual Redistributable. Novější verze přepíše starší verzi, která je již nainstalována. Pokud máte vizuál C++ distribuovatelné ze sady visual Studio 2015 nebo 2017 a později nainstalujete visual Studio 2019, verze 2019 přepíše starší verzi. Protože se ujistěte, že nejnovější verze obsahuje všechny nejnovější funkce a opravy chyb (včetně oprav zabezpečení), vždycky doporučujeme, abyste provedli upgrade na nejnovější dostupnou verzi.

Obdobně neumožníme instalaci starší verze vizuálu C++ Redistributable na počítač, na kterém je už nainstalovaná novější verze. Instalace vizuálu C++ Redistributable ze sady visual Studio 2015 nebo 2017 na počítači, který už má verzi 2019, se spustí Chyba instalace. Tato chyba se podobá následujícímu:

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Tato chyba je záměrné. Doporučujeme zachovat nainstalovanou nejnovější verzi.

## <a name="see-also"></a>Viz také:

* [Historie C++ vizuálních změn](../porting/visual-cpp-change-history-2003-2015.md)
* [Nejnovější podporované vizuální C++ redistribuovatelné soubory ke stažení](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
