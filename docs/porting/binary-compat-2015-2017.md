---
title: C++Binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019
ms.date: 10/17/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 6365ded349ad08a167b76ca9f6ab43e6e7752987
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587904"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++Binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019

V Visual Studio 2013 a starších verzích nebyla zaručena binární kompatibilita mezi soubory objektů (OBJs), statickými knihovnami (knihovny), dynamickými knihovnami (DLL) a spustitelnými soubory (exe) sestavenými pomocí různých verzí sady nástrojů kompilátoru a běhových knihoven. 

V sadě Visual Studio 2015 nebo novější je C++ hlavní číslo sady nástrojů 14 (V140 for visual Studio 2015, V141 for visual Studio 2017 a V142 for visual Studio 2019). To odráží skutečnost, že běhové knihovny i aplikace zkompilované v obou verzích kompilátoru jsou binární kompatibilní. To znamená, že pokud máte knihovnu třetí strany vytvořenou v rámci sady Visual Studio 2015, nemusíte ji znovu kompilovat, aby ji bylo možné využívat z aplikace vytvořené pomocí sady Visual Studio 2017 nebo Visual Studio 2019.

Jedinou výjimkou z tohoto pravidla je, že statické knihovny nebo soubory objektů, které jsou kompilovány s přepínačem `/GL` kompilátoru, nejsou binární kompatibilní. 

Když kombinujete binární soubory sestavené s různými podporovanými verzemi sady nástrojů MSVC, vizuál C++ , ve kterém je vaše aplikace spuštěná, nemůže být starší než kterákoli z verzí sady nástrojů, která se používá k sestavení vaší aplikace nebo všech knihoven, které spotřebovává. 

## <a name="upgrade-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Upgrade Microsoft Visual C++ Redistributable ze sady visual Studio 2015 nebo 2017 na visual Studio 2019

Vzhledem k tomu, že jsme zachovali binární kompatibilitu a zachovali hlavní verzi (14) stejné pro C++ Visual Redistributable pro visual Studio 2015, 2017 a 2019, můžete z nich kdykoli nainstalovat jenom jednu C++ verzi sady Visual Redistributable. Novější verze přepíše starší verzi, která je nainstalována. Pokud máte vizuál C++ distribuovatelné ze sady visual Studio 2015 nebo 2017 a později nainstalujete 2019, bude verze 2019 přepsat starší verzi. Protože zajišťujeme, že nejnovější verze budou mít všechny nejnovější funkce a opravy chyb, včetně oprav zabezpečení, vždycky doporučujeme upgradovat na nejnovější dostupnou verzi.

Podobně nepovolujeme instalaci starší verze vizuálu C++ Redistributable na počítač, kde novější už existuje. Instalace vizuálu C++ Redistributable ze sady visual Studio 2015 nebo 2017 na počítači, který již má 2019, bude mít za následek selhání instalace. Tato chyba bude vypadat přibližně takto:

```
*0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.*.
```

Tato chyba je záměrné. Doporučujeme ponechat si nejnovějšího nainstalovaného.

## <a name="see-also"></a>Viz také:

* [Historie C++ vizuálních změn](../porting/visual-cpp-change-history-2003-2015.md)
* [Nejnovější podporované vizuální C++ redistribuovatelné soubory ke stažení](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
