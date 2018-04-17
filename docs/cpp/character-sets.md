---
title: Znakových sad | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81b1046ea7588a6cc5eb3274473f4e4bee9daccd
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="character-sets"></a>Znakové sady
Text programu C++ je uložen ve zdrojových souborech, které používají konkrétní znaky kódování. Standardní C++ určuje základní zdrojová znaková sada pro zdrojové soubory a spuštění základní znaková sada pro zkompilované soubory. Visual C++ umožňuje další sadu znaků specifická pro národní prostředí pro použití ve zdrojových souborech a zkompilované soubory.  
  
## <a name="character-sets"></a>Znakové sady  
 Určuje C++ standard *základní zdroj znakovou sadu* která může být použita ve zdrojových souborech. K reprezentaci znaků mimo tuto sadu, lze zadat další znaky pomocí *universal znak název*. Při kompilaci, *znaková sada spuštění základní* a *základní provádění široká charakterová sada* představují znaky a řetězce, které se mohou objevit v programu. Implementace Visual C++ umožňuje dalších znaků v zdrojový kód a zkompilovaný kód.  
  
### <a name="basic-source-character-set"></a>Základní zdrojové znakové sady  
 *Základní zdroj znakovou sadu* obsahuje 96 znaky, které je možné použít zdrojové soubory. Tato sada obsahuje znak, vodorovné karta, vertikální tabulátor, formuláře kanálu a nový řádek řídicí znaky, a to sada grafické znaky:  
  
 `a b c d e f g h i j k l m n o p q r s t u v w x y z`  
  
 `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`  
  
 `0 1 2 3 4 5 6 7 8 9`  
  
 `_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`  
  
 **Konkrétní Microsoft**  
  
 Zahrnuje Visual C++ `$` znak jako člen skupiny základní zdroj znakovou sadu. Visual C++ také umožňuje další sadu znaků, který má být používány zdrojové soubory, založené na kódování souborů. Visual Studio ve výchozím nastavení ukládá zdrojové soubory pomocí výchozí znaková stránka. Pokud zdrojové soubory jsou ukládány pomocí znaková stránka národního prostředí konkrétní nebo codepage znakové sady Unicode, Visual C++ umožňuje používat znaky této stránce kódu ve zdrojovém kódu, s výjimkou kódy ovládacího prvku není explicitně povolená v znak základní zdroje nastavit. Například můžete umístit japonské znaky v komentáře, identifikátory nebo textové literály, pokud uložíte soubor pomocí japonské kódové stránky. Visual C++ neumožňuje sekvence znaků, které nelze přeložit na platný více-bajtové znaky nebo body kódu Unicode. V závislosti na – možnosti kompilátoru se mohou objevit všechny povolený počet znaků v identifikátory. Další informace najdete v tématu [identifikátory](../cpp/identifiers-cpp.md).  
  
 **Konkrétní Microsoft END**  
  
### <a name="universal-character-names"></a>Univerzální názvy znaků  
 Protože mnoho více znaků, než jsou zadány ve znakové sadě základní zdroj můžete použít programy C++, můžete zadat tyto znaky v přenosný způsob, jak pomocí *univerzální názvy znaků*. Název universal znak se skládá z posloupnosti znaků, které představují bod kódování Unicode.  Tyto trvat dva formuláře. Použití `\UNNNNNNNN` představující bod kódování Unicode formuláře U + NNNNNNNN, kde je NNNNNNNN číslo bodu hexadecimální kódem. Použití čtyř číslic `\uNNNN` představující bod kódování Unicode U + 0000NNNN ve formuláři.  
  
 Univerzální názvy znaků lze v identifikátory a literály řetězce a znak. Představuje bod náhradní kódu v rozsahu 0xD800 0xDFFF nelze použít název universal znak. Místo toho použijte čárky požadované kódu. kompilátor automaticky vygeneruje všechny požadované náhrady. Další omezení platí pro názvy universal znaků, které mohou být používány identifikátory. Další informace najdete v tématu [identifikátory](../cpp/identifiers-cpp.md) a [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md).  
  
 **Konkrétní Microsoft**  
  
 Visual C++ compiler zpracovává znak v universal znak název literálu formuláři a zcela zaměnitelným významem. Můžete například deklarovat identifikátor použití universal znak název formuláře a použít ho v literálu formuláře:  
  
```cpp  
auto \u30AD = 42; // \u30AD is 'キ'  
if (キ == 42) return true; // \u30AD and キ are the same to the compiler  
  
```  
  
 Formát rozšířených znaků do schránky systému Windows je specifické pro aplikaci nastavení národního prostředí. Vyjímání a vkládání do kódu z další aplikace, tyto znaky mohou zavést kódování neočekávaný znak. To může způsobit chyby při analýze žádné viditelné příčina ve vašem kódu. Doporučujeme, abyste nastavili vaší zdrojového souboru kódování Unicode codepage před vložením rozšířené znaky. Doporučujeme také můžete vygenerovat rozšířené znaky pomocí editoru IME nebo aplikace Mapa znaků.  
  
 **Konkrétní Microsoft END**  
  
### <a name="basic-execution-character-set"></a>Znaková sada spuštění základní  
 *Znaková sada spuštění základní* a *základní provádění široká charakterová sada* obsahovat všechny znaky znakové sady základní zdroj a řídicí znaky, které představují výstrahy BACKSPACE, návrat na začátek a znak hodnoty null.   *Znaková sada spuštění* a *provádění široká charakterová sada* jsou nadmnožiny základní sady. Obsahují znaky definované implementací zdroj mimo základní zdroj znakovou sadu. Znaková sada spuštění má znázornění specifická pro národní prostředí.