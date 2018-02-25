---
title: "komentáře (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1062923f50470a2238af21676c4137fac241905
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="comment-cc"></a>comment (C/C++)
Záznam komentář umístí do k objektu souboru nebo spustitelného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## <a name="remarks"></a>Poznámky  
 *Typ komentáře* je jedním z předdefinované identifikátory, které jsou popsané níže, který určuje typ záznamu komentář. Volitelné `commentstring` je řetězcový literál, který poskytuje další informace pro některé typy komentář. Protože `commentstring` je řetězec literálu, je dodržuje všechna pravidla pro textové literály s ohledem na řídicí znaky uvozovek embedded (**"**) a zřetězení.  
  
 **compiler**  
 Název a verze počet kompilátor umístí do souboru objektu. Tento záznam komentář je ignorován v linkeru. Pokud zadáte `commentstring` parametr pro tento typ záznamu, kompilátor vygeneruje upozornění.  
  
 **exestr**  
 Místech `commentstring` do souboru objektu. Tento řetězec je v době spojení umístěna ve spustitelném souboru. Řetězec není načten do paměti, když je načten spustitelný soubor. je však možné najít s programem, který vyhledá tisknutelná řetězců v souborech. Vložit číslo verze nebo podobné informace do spustitelného souboru je jedno použití pro tento typ záznamu komentář.  
  
 `exestr` je zastaralá a budou odebrány v budoucí verzi; linkeru nezpracovává záznam komentář.  
  
 **lib**  
 Záznam knihovny vyhledávání umístí do souboru objektu. Tento typ komentáře musí být doplněn `commentstring` parametr obsahující název (a případně cestu) knihovny, která chcete linkeru pro vyhledávání. Výchozí knihovna vyhledávání záznamy v souboru objektu; následuje název knihovny propojovací prohledává pro tuto knihovnu stejně, jako by vám měl s názvem ho na příkazovém řádku za předpokladu, že knihovna není zadaný s [/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md). Více záznamů knihovny vyhledávání můžete umístit do stejného zdrojového souboru; Každý záznam se zobrazí v souboru objektu ve stejném pořadí, ve kterém je došlo ve zdrojovém souboru.  
  
 Pokud pořadí výchozí knihovna a přidané knihovny je důležité, kompilování pomocí [/Zl](../build/reference/zl-omit-default-library-name.md) přepínač zabrání názvu výchozí knihovny je uskutečnění v objektu modulu. Druhý comment – Direktiva pragma pak slouží k vložení názvu výchozí knihovny za přidané knihovny. Knihovny uvedené s těmito direktivy se zobrazí v objektu modulu ve stejném pořadí, které se nacházejí ve zdrojovém kódu.  
  
 **linker**  
 Místech [– možnost linkeru](../build/reference/linker-options.md) do souboru objektu. Tento typ komentáře můžete použít k určení propojovacího místo předání do příkazového řádku nebo zadání ve vývojovém prostředí. Například můžete zadat / include – možnost vynutit zahrnutí symbol:  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
 Jenom následující (*typ komentáře*) jsou k dispozici mají být předány identifikátor linkeru linkeru možnosti:  
  
-   [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
-   [/EXPORT](../build/reference/export-exports-a-function.md)  
  
-   [/ INCLUDE](../build/reference/include-force-symbol-references.md)  
  
-   [/ MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
-   [/MERGE](../build/reference/merge-combine-sections.md)  
  
-   [/ SECTION](../build/reference/section-specify-section-attributes.md)  
  
 **user**  
 Obecné komentář umístí do souboru objektu. `commentstring` Parametr obsahuje text poznámky. Tento záznam komentář je ignorován v linkeru.  
  
 Následující – Direktiva pragma způsobí, že linkeru pro vyhledávání EMAPI. Knihovna LIB při propojení. Propojovací prohledává nejprve v aktuální pracovní adresář a pak v cestě určeném v proměnné prostředí LIB.  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
 Následující – Direktiva pragma způsobí, že kompilátor umístit název a verze počet kompilátoru do souboru objektu:  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
>  Pro komentáře trvají `commentstring` parametr, můžete použít makra v jakémkoli místě, kde byste použili řetězcový literál, za předpokladu, že se rozbalí makro pro řetězcový literál. Můžete také řetězení libovolnou kombinaci textové literály a makra rozbalte pro textové literály. Například je přijatelné následující příkaz:  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)