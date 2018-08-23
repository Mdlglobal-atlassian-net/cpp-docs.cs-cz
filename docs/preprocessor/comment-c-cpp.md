---
title: komentáře (C/C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.comment
- comment_CPP
dev_langs:
- C++
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d90cdb457e09ca51f14828daf5b7fb2676cb0db
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465303"
---
# <a name="comment-cc"></a>comment (C/C++)
Umístí záznam komentář do objektu souboru nebo spustitelný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## <a name="remarks"></a>Poznámky 

*Typů komentář* je jedním z předdefinované identifikátory, které jsou popsané níže, který určuje typ záznamu komentář. Volitelný *commentstring* není řetězcový literál, který poskytuje další informace o některých typů komentář. Protože *commentstring* je textový literál, dodržuje všechna pravidla pro řetězcové literály s ohledem na řídicí znaky, uvozovky (`"`) a zřetězení.  
  
### <a name="compiler"></a>– kompilátor  
Umístí název a číslo verze kompilátoru do souboru objektu. Tento záznam komentář se ignoruje linkerem. Pokud zadáte *commentstring* parametr pro tento typ záznamu, kompilátor vygeneruje upozornění.  
  
### <a name="exestr"></a>exestr  
Místa *commentstring* do souboru objektu. V době spojení, tento řetězec nachází ve spustitelném souboru. Řetězec není načtena do paměti při načtení spustitelného souboru; je však možné najít s programem, který vyhledá tisknutelný řetězce v souborech. Jedno použití pro tento typ záznamu komentář, je vložit číslo verze nebo podobné informace ve spustitelném souboru.  
  
`exestr` je zastaralá a bude v budoucí verzi; odebrána linker nezpracovává záznam komentář.  
  
### <a name="lib"></a>lib  
Záznam knihovny vyhledávání umístí do souboru objektu. Tento typ komentáře musí být doplněny *commentstring* parametr obsahující název (a případně cestu) knihovny, který chcete, aby linkeru, aby hledání. Výchozí knihovna hledání záznamy v souboru objektů; následuje název knihovny propojovací program vyhledá pro tuto knihovnu stejně, jako by vám měl s názvem ho v příkazovém řádku za předpokladu, že není zadaný knihovny s [: / NODEFAULTLIB](../build/reference/nodefaultlib-ignore-libraries.md). Umístíte více záznamů vyhledávání knihovny ve stejném zdrojovém souboru; Každý záznam se zobrazí v souboru objektu ve stejném pořadí, ve kterém dochází ve zdrojovém souboru.  
  
Pokud je důležité pořadí výchozí knihovny a přidání knihovny, kompilaci [/Zl](../build/reference/zl-omit-default-library-name.md) přepínač zabrání názvu výchozí knihovny umístěných v modulu objektu. Druhý comment – Direktiva pragma pak lze použít pro vložení názvu výchozí knihovny po přidání knihovny. Knihoven uvedené pomocí direktivy pragma se zobrazí v modulu objektu ve stejném pořadí, ve kterém se nacházejí ve zdrojovém kódu.  
  
### <a name="linker"></a>linker  
Místa [– možnost linkeru](../build/reference/linker-options.md) do souboru objektu. Tento typ komentáře můžete použít k určení linkeru namísto předávání do příkazového řádku nebo zadání ve vývojovém prostředí. Například můžete zadat / include – možnost vynutit zahrnutí symbol:  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
Pouze následující (*typů komentář*) jsou k dispozici identifikátor propojovacího programu předat možnosti linkeru:  
  
- [/ DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
- [/EXPORT](../build/reference/export-exports-a-function.md)  
  
- [/ INCLUDE](../build/reference/include-force-symbol-references.md)  
  
- [/ MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
- [/MERGE](../build/reference/merge-combine-sections.md)  
  
- [/ SECTION](../build/reference/section-specify-section-attributes.md)  
  
### <a name="user"></a>uživatel  
Obecné komentáře umístí do souboru objektu. *Commentstring* parametr obsahuje text komentáře. Tento záznam komentář se ignoruje linkerem.  
  
Následující direktivy pragma přikazuje linkeru pro hledání EMAPI. Knihovny LIB při propojování. Propojovací program vyhledá první v aktuálním pracovním adresáři a poté v cestě zadané v proměnné prostředí LIB.  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
Následující direktivy pragma způsobí, že kompilátor umístí název a číslo verze kompilátoru do souboru objektu:  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
> Pro komentáře trvají *commentstring* parametr, můžete použít makra v jakémkoli místě, kde by použít textový literál, za předpokladu, že se makro rozbalí na řetězcový literál. Také lze zřetězit libovolnou kombinaci řetězcové literály a makra, která rozšířit na řetězcové literály. Například následující příkaz je přijatelné:  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)