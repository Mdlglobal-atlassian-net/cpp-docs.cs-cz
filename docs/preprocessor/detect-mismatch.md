---
title: detect_mismatch | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f165d24dc1a3044fb89474aef58a2992fa6feed9
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465470"
---
# <a name="detectmismatch"></a>detect_mismatch
Umístí do objektu záznam. Linker zkontroluje tyto záznamy a vyhledá potenciální problémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>Poznámky  
 
Při propojení projektu vyvolá linker chybu `LNK2038`, pokud projekt obsahuje dva objekty, které mají stejný název `name`, ale každý má jinou hodnotu `value`. Pomocí této direktivy pragma lze zabránit v propojení nekonzistentních objektových souborů.  
  
Název a hodnota jsou řetězcové literály a dodržují pravidla pro řetězcové literály, pokud jde o řídicí znaky a zřetězení. Jsou malá a velká písmena a nemůže obsahovat čárku, znaménko rovnosti, uvozovky, nebo **null** znak.  
  
## <a name="example"></a>Příklad  
 
Tento příklad vytvoří dva soubory, které mají různá čísla verze pro stejný popisek verze.  
  
```cpp  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
Jsou-li oba soubory zkompilovány pomocí příkazového řádku `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, dojde k chybě `LNK2038`.  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)