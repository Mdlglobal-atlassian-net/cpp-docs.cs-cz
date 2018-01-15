---
title: execution_character_set | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs: C++
helpviewer_keywords: pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1064f5cf97ba6b919e718c60c8346e86d643ced
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="executioncharacterset"></a>execution_character_set
Určuje znaková sada spuštění, který se používá pro literály řetězce a znak. Tato direktiva není potřeba pro literály označené jako předponu u8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma execution_character_set("target")  
```  
  
#### <a name="parameters"></a>Parametry  
 `target`  
 Určuje znaková sada spuštění cíl. Se v současné době pouze provádění cílů nastavit podporované "znakové sady utf-8".  
  
## <a name="remarks"></a>Poznámky  
 Tato direktiva kompilátoru je zastaralé od verze Visual Studio 2015 Update 2. Doporučujeme použít **/execution-charset:utf-8** nebo **/utf-8** – možnosti kompilátoru společně s použitím `u8` předponu na úzké řetězec a znakové literály obsahující rozšířené znaky. Další informace o `u8` předpony najdete v tématu [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md). Další informace o možnostech kompilátoru najdete v tématu [/execution-charset (nastavit provádění znaková sada)](../build/reference/execution-charset-set-execution-character-set.md) a [/utf-8 (nastavit zdroj a spustitelný soubor znakových sad na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).  
  
 `#pragma execution_character_set("utf-8")` – Direktiva určuje kompilátor kódování úzké znak a úzké textové literály ve zdrojovém kódu jako UTF-8 ve spustitelném souboru. Toto kódování výstup je nezávislá kódování souboru zdroje používat.  
  
 Ve výchozím nastavení kompilátor kóduje úzké znaky a řetězce úzké pomocí aktuálního kódu stránky jako znaková sada spuštění. To znamená, že znaky Unicode nebo DBCS v literál, které jsou mimo rozsah aktuální znaková stránka se převedou na výchozí znakovou nahrazení ve výstupu. Znaky kódování Unicode a DBCS se zkrátí na jejich nejnižší bajtů. Toto je skoro určitě není co chcete. Můžete zadat kódování UTF-8 pro literály ve zdrojovém souboru pomocí `u8` předponu. Kompilátor předá tyto řetězce formátu UTF-8 ve výstupu beze změny. Úzké znakové literály předponu pomocí u8 se musí vejít do jednoho bajtu nebo se zkrátí na výstup.  
  
 Ve výchozím nastavení Visual Studio použije aktuální znakovou stránku jako zdroj znaková sada používaná k interpretaci vašeho zdrojového kódu pro výstup. Přečtení soubor v sadě Visual Studio interpretovat podle aktuální znaková stránka Pokud byla nastavena znaková stránka souboru, nebo pokud na začátku souboru zjištění značky pořadí bajtů (BOM) nebo UTF-16 znaků. Protože UTF-8 se nedá nastavit jako aktuální znakové stránky, když automatické zjišťování dojde zdrojový soubor v kódování UTF-8 bez Kusovník, předpokládá Visual Studio, jsou zakódovány pomocí aktuálního kódu stránky. Znaky v souboru zdroje, které jsou mimo rozsah pro zadaný nebo automaticky zjistil, že znaková stránka může způsobit chyby a varování kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/Execution-Charset (nastavit provádění znaková sada)](../build/reference/execution-charset-set-execution-character-set.md)   
 [/UTF-8 (nastavit zdroj a spustitelný soubor znakových sad na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)