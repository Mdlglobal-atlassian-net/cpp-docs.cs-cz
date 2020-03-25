---
title: Rozšíření Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: a2d0846e55122f177b4868c2e80c4f1d27267f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179403"
---
# <a name="microsoft-extensions"></a>Rozšíření Microsoft

*příkaz ASM*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm***sestavení-instrukce* **;** <sub>výslovný souhlas</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *Assembly-Instruction-list* **};** <sub>výslovný souhlas</sub>

*seznam instrukcí pro sestavení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sestavení-instrukce* **;** <sub>výslovný souhlas</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sestavení-instrukce* **;** *Assembly-instrukces-list* **;** <sub>výslovný souhlas</sub>

*MS-modifikátor-seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*MS-modifikátor* *MS-modifikátor-seznam*<sub>opt</sub>

*MS-modifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__syscall** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__oldcall** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__unaligned** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*na základě modifikátoru*

*založený na modifikátorech*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__based (** *podle typu* **)**

*založený na typu*:<br/>
&nbsp;&nbsp;&nbsp;*název* &nbsp;
