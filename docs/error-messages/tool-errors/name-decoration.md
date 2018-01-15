---
title: "Název Decoration | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f780b91d7d58ecdfc9b2af4295c76253357f8e66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="name-decoration"></a>Dekorování názvů
Dekorování názvů obvykle odkazuje na zásady vytváření názvů C++, ale můžete použít pro několik případů C také. Ve výchozím nastavení C++ používá název funkce, parametry a návratový typ pro vytvoření linkeru název funkce. Vezměte v úvahu následující funkce:  
  
```  
void CALLTYPE test(void)  
```  
  
 Následující tabulka uvádí název linkeru pro různé konvence volání.  
  
|Konvence volání|extern "C" nebo .c souboru|sada, .cxx nebo /TP|  
|------------------------|---------------------------|------------------------|  
|Zásady vytváření názvů jazyka C (`__cdecl`)|_test|? testování@ZAXXZ|  
|Zásady vytváření názvů fastcall (`__fastcall`)|@test@0|? testování@YIXXZ|  
|Standardní zásady vytváření názvů volání (`__stdcall`)|_test@0|? testování@YGXXZ|  
|Zásady vytváření názvů Vectorcall (`__vectorcall`)|testování @@0|? testování@YQXXZ|  
  
 Volání funkce C z jazyka C++ pomocí extern "C". Extern "C" vynutí použití zásady vytváření názvů jazyka C pro jiné třídy funkcí jazyka C++. Mějte na paměti přepínačů kompilátoru **/Tc** nebo **/Tp**, který oznámení kompilátoru ignorovat příponu názvu souboru a kompilaci souboru jako jazyka C nebo C++, v uvedeném pořadí. Tyto možnosti může způsobit názvy, které neočekáváte.  
  
 Tato chyba může také způsobit s prototypy funkcí, které mají neodpovídající parametry. Dekorování názvů začleňuje do konečné dekorované funkce název parametry funkce. Volání funkce s typy parametrů, které neodpovídají definicím v deklaraci funkce může také způsobit LNK2001.  
  
 Není aktuálně standard pro pojmenování mezi kompilátoru dodavateli nebo i mezi různými verzemi kompilátor C++. Proto propojení soubory objektů kompilovat s jinými kompilátory nemusí poskytovat stejné schéma pojmenování a proto způsobí, že chyby definicí.  
  
## <a name="see-also"></a>Viz také  
 [Chyba linkerů LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)