---
title: Rozšíření Microsoft | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5699ce82a6e8537f12da50fdcb8288da167ecca3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752236"
---
# <a name="microsoft-extensions"></a>Rozšíření Microsoft

*příkazu asm*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***instrukci sestavení* **;** <sub>optimalizované  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***sestavení seznam instrukcí-***};** <sub>optimalizované    </sub>

*sestavení seznam instrukcí-*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukci sestavení* **;** <sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukci sestavení* **;** *sestavení seznam instrukcí-* **;** <sub>optimalizované</sub>

*MS seznam-modifikátorů-*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Modifikátor MS* *ms seznam-modifikátorů-*<sub>optimalizované</sub>

*Modifikátor MS*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** (vyhrazeno pro budoucí implementace)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*na základě – modifikátor*

*na základě modifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *základní typ* **)**

*na základě typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Jméno*