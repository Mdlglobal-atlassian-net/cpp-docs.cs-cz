---
title: "Vnitřní funkce kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20b1416eacc6fa31c5e41b4a0539ce9ccbd99f88
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="compiler-intrinsics"></a>Vnitřní funkce kompilátoru
Většina funkcí jsou obsaženy v knihovnách, ale některé funkce, které jsou integrované v (to znamená, vnitřní) pro kompilátor. Tyto jsou označovány jako vnitřní funkce nebo vnitřní funkce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je funkce vnitřní, kód pro tuto funkci je obvykle připojen, není zpomalován režií volání funkce a vysoce efektivní počítače pokyny pro vypuštění pro tuto funkci povolil. Vnitřní je často rychlejší než ekvivalentní vloženého sestavení, protože okně Optimalizace má integrovanou znalost tak, kolik – vnitřní prvky, takže některé optimalizace může být k dispozici, nejsou k dispozici při použití vloženého sestavení. Okně Optimalizace můžete také rozšířit vnitřní odlišně, jinak zarovnat vyrovnávací paměti nebo provádět další úpravy v závislosti na kontextu a argumentů volání.  
  
 Použití vnitřní funkce ovlivňuje přenositelnost kódu, protože vnitřní funkce, které jsou k dispozici v jazyce Visual C++ nemusí být k dispozici, pokud kód je kompilovat s jinými kompilátory a vnitřní některé funkce, které můžou být dostupné pro některé cílové architektury nejsou k dispozici pro všechny architektury. Vnitřní funkce jsou však obvykle obecnější než vložené sestavení. Vnitřní objekty je nutné 64bitové architektury, kde se nepodporuje vložené sestavení.  
  
 Vnitřní některé funkce, jako například `__assume` a `__ReadWriteBarrier`, zadejte informace pro kompilátor, které ovlivňují chování pro optimalizaci.  
  
 Některé – vnitřní prvky jsou k dispozici pouze jako vnitřní objekty a některé jsou k dispozici jak v vnitřní implementace a funkce. Můžete určit, aby kompilátor používal vnitřní implementace v jednom ze dvou způsobů, v závislosti na tom, jestli chcete povolit jenom určité funkce, nebo chcete povolit všechny vnitřní funkce. První způsob je použití `#pragma intrinsic(` *vnitřní funkce název list*`)`. – Direktiva pragma slouží k určení vnitřní jedné nebo více vnitřní funkce oddělených čárkami. Druhý je použití [/Oi (Generovat vnitřní funkce)](../build/reference/oi-generate-intrinsic-functions.md) – možnost kompilátoru, která zpřístupňuje vnitřní všechny funkce na dané platformy. V části **/Oi**, použijte `#pragma function(` *vnitřní funkce název list* `)` vynutit volání funkce, který má být použit místo vnitřní. Pokud v dokumentaci pro konkrétní vnitřní zaznamená rutiny se pouze k dispozici jako vnitřní, pak bez ohledu na to, jestli se používá vnitřní implementace **/Oi** nebo `#pragma intrinsic` je zadán. Ve všech případech **/Oi** nebo `#pragma intrinsic` povoluje, ale bez vynucení, optimalizátor používat vnitřní. Pro optimalizaci stále můžete volat funkce.  
  
 Funkce některé standardní knihovny jazyka C/C++ jsou k dispozici v vnitřní implementace na některé architektury. Při volání funkce CRT, pokud se používá vnitřní implementace **/Oi** je zadán v příkazovém řádku.  
  
 Soubor hlaviček \<intrin.h >, je k dispozici, který deklaruje prototypy pro běžné vnitřní funkce. Vnitřní funkce specifické pro výrobce jsou k dispozici v \<immintrin.h > a \<ammintrin.h > soubory hlaviček. Kromě toho některé hlavičky Windows deklarovat funkce, které mapují na vnitřní kompilátor.  
  
 Následující části uvádějí všechny vnitřní funkce, které jsou dostupné na různých architektury. Další informace o fungování vnitřní objekty na vaše konkrétní cílový procesoru naleznete v dokumentaci od výrobce odkaz.  
  
-   [ARM – vnitřní prvky](../intrinsics/arm-intrinsics.md)  
  
-   [x86 – seznam vnitřních objektů](../intrinsics/x86-intrinsics-list.md)  
  
-   [x64 (amd64) – seznam vnitřních objektů](../intrinsics/x64-amd64-intrinsics-list.md)  
  
-   [Vnitřní objekty dostupné ve všech architekturách](../intrinsics/intrinsics-available-on-all-architectures.md)  
  
-   [Abecední seznam vnitřních funkcí](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace assembleru ARM](../assembler/arm/arm-assembler-reference.md)   
 [Microsoft Macro Assembler – referenční dokumentace](../assembler/masm/microsoft-macro-assembler-reference.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)