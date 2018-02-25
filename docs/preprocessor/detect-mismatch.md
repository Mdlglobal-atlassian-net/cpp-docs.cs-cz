---
title: detect_mismatch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 875b6980a3c55c07b5765d6d0fc12be1796ee3a3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="detectmismatch"></a>detect_mismatch
Umístí do objektu záznam. Linker zkontroluje tyto záznamy a vyhledá potenciální problémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>Poznámky  
 Při propojení projektu vyvolá linker chybu `LNK2038`, pokud projekt obsahuje dva objekty, které mají stejný název `name`, ale každý má jinou hodnotu `value`. Pomocí této direktivy pragma lze zabránit v propojení nekonzistentních objektových souborů.  
  
 Název a hodnota jsou řetězcové literály a dodržují pravidla pro řetězcové literály, pokud jde o řídicí znaky a zřetězení. Rozlišují velká a malá písmena a nesmějí obsahovat čárku, znaménko rovnosti, uvozovky nebo znak `null`.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří dva soubory, které mají různá čísla verze pro stejný popisek verze.  
  
```  
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