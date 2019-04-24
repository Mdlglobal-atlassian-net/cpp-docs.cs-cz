---
title: Rozšíření Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301770"
---
# <a name="microsoft-extensions"></a>Rozšíření Microsoft

*příkazu asm*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***instrukci sestavení* **;** <sub>optimalizované  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***sestavení seznam instrukcí-***};** <sub>optimalizované    </sub>

*sestavení seznam instrukcí-*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukci sestavení* **;** <sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukci sestavení* **;** *sestavení seznam instrukcí-* **;** <sub>optimalizované</sub>

*ms-modifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms-modifier* *ms-modifier-list*<sub>opt</sub>

*ms-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*based-modifier*

*based-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *základní typ* **)**

*na základě typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Jméno*