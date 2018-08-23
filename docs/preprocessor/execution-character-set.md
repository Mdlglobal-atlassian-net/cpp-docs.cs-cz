---
title: execution_character_set | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs:
- C++
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f6851813172c39cd3c8c5dfe19b4d12ba81d090
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465650"
---
# <a name="executioncharacterset"></a>execution_character_set
Určuje znakovou sadu spuštění použitou pro literálech řetězců a znaků. Tato direktiva, není nutná pro literály označené předponou u8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma execution_character_set("target")  
```  
  
### <a name="parameters"></a>Parametry  
*Cíl*  
Určuje cílový znaková sada spuštění. Aktuálně je pouze provádění cílů v nastavení podporovaná "utf-8".  
  
## <a name="remarks"></a>Poznámky  
 
Tato direktiva kompilátoru je zastaralé od verze Visual Studio 2015 Update 2. Doporučujeme použít `/execution-charset:utf-8` nebo `/utf-8` – možnosti kompilátoru spolu s použitím `u8` předpony u úzký znakové a řetězcové literály, které obsahují rozšířené znaky. Další informace o `u8` předpony, přečtěte si téma [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md). Další informace o možnostech kompilátoru najdete v tématu [/Execution-Charset (nastavení znakové sady spuštění)](../build/reference/execution-charset-set-execution-character-set.md) a [/UTF-8 (nastavení zdrojové a spustitelné znakové sady UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).  
  
`#pragma execution_character_set("utf-8")` – Direktiva instruuje kompilátor, aby kódovat úzkých znaků a literály úzký řetězcový ve zdrojovém kódu jako UTF-8 ve spustitelném souboru. Kódování výstupu je nezávislá kódování souboru zdroje používá.  
  
Ve výchozím nastavení kompilátor kóduje úzkých znaků a úzké řetězce pomocí aktuální znakové stránce jako znaková sada spuštění. To znamená, že Unicode nebo DBCS znaků literál, které jsou mimo rozsah aktuální znakové stránce jsou převedeny na výchozí znak nahrazení ve výstupu. Znaky kódování Unicode a DBCS se zkrátí na jejich nejnižší bajt. Toto je téměř jistě není co chcete. Můžete určit kódování UTF-8 s použitím pro literály ve zdrojovém souboru `u8` předponu. Kompilátor předá tyto řetězce UTF-8 na výstup beze změny. Úzký znakové literály předponu u8 se musí vejít do jeden bajt, nebo se zkrátí na výstupu.  
  
Ve výchozím nastavení používá Visual Studio jako zdrojovou znakovou sadou použité k interpretaci zdrojový kód pro výstup aktuální znakové stránce. Přečtení souboru v sadě Visual Studio interpretovat podle aktuální znakové stránce Pokud byla nastavena na znakovou stránku souboru, nebo pokud jsou zjištěny značka pořadí bajtů (BOM) nebo UTF-16 znaků na začátku souboru. Protože UTF-8 nelze nastavit jako aktuální znakové stránce, když se automatická detekce setká zdrojových souborů s kódováním UTF-8 bez BOM, Visual Studio se předpokládá, že jsou zakódovány pomocí aktuální znakové stránce. Znaky ve zdrojovém souboru, které jsou mimo rozsah pro zadaný nebo automaticky zjištěna znaková stránka může způsobit, že kompilátor varování a chyby.  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
[/ Execution-Charset (nastavení znakové sady spuštění)](../build/reference/execution-charset-set-execution-character-set.md)   
[/utf-8 (nastavení zdrojové znakové sady a spustitelné znakové sady na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)