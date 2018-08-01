---
title: Znakové sady | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/12/2018
ms.technology:
- cpp-language
ms.topic: language-reference
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25370d7b7e5ddf460ace1ce349c9fc501feb2343
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407072"
---
# <a name="character-sets"></a>Znakové sady
Text programu v jazyce C++ je uložen ve zdrojových souborech, které používají určitý znak kódování. Standard jazyka C++ určuje základní zdrojové znakové sady zdrojových souborů a základním provedení znakové sady pro zkompilované soubory. Visual C++ umožňuje další sadu znaků specifických pro národní prostředí pro použití ve zdrojových souborech a zkompilované soubory.  
  
## <a name="character-sets"></a>Znakové sady  
 Určuje standard jazyka C++ *základní sada zdrojových znaků* , která může být použita ve zdrojových souborech. K reprezentaci znaků mimo tuto sadu, můžete zadat další znaky pomocí *univerzální název znaku*. Při kompilaci, *základní znakové sadě spuštění* a *základním provedení široká charakterová sada* reprezentaci znaků a řetězce, které se mohou objevit v programu. Implementace jazyka Visual C++ umožňuje další znaky ve zdrojovém kódu a zkompilovaného kódu.  
  
### <a name="basic-source-character-set"></a>Základní sada zdrojových znaků  
 *Základní sada zdrojových znaků* se skládá z 96 znaků, které lze použít ve zdrojových souborech. Tato sada obsahuje znak, horizontálního tabulátoru, vertikálního tabulátoru, posun a nový řádek řídicí znaky, a to sadu grafické znaky:  
  
 `a b c d e f g h i j k l m n o p q r s t u v w x y z`  
  
 `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`  
  
 `0 1 2 3 4 5 6 7 8 9`  
  
 `_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`  
  
 **Specifické pro Microsoft**  
  
 Visual C++ obsahuje `$` znak jako člen základní zdrojové znakové sady. Visual C++ umožňuje také další sadu znaků, které mají použít ve zdrojových souborech založené na kódování souboru. Ve výchozím nastavení Visual Studio ukládá zdrojové soubory s použitím výchozí znakovou stránku. Pokud zdrojové soubory jsou uloženy ve znakové stránce specifických pro národní prostředí nebo znaková stránka Unicode, Visual C++ umožňuje používat znaky tuto znakovou stránku ve zdrojovém kódu, s výjimkou řídicích kódů nejsou explicitně povolená v základní zdrojové znakové nastavit. Například můžete vložit japonské znaky komentáře, identifikátory nebo řetězcové literály, při uložení souboru pomocí japonské znakovou stránku. Visual C++ nepovoluje sekvence znaků, které nelze převést na platné vícebajtové znaky nebo kódové body sady Unicode. V závislosti na možnostech kompilátoru můžou objevit všechny povolené znaky v identifikátory. Další informace najdete v tématu [identifikátory](../cpp/identifiers-cpp.md).  
  
 **Specifické pro END Microsoft**  
  
### <a name="universal-character-names"></a>Univerzální názvy znaků  
 Protože programy v jazyce C++ můžete použít mnoho více znaků, než úlohy uvedené v základní zdrojové znakové sady, můžete zadat tyto znaky v přenosný způsob, jak pomocí *univerzální názvy znaků*. Univerzální název znaku se skládá z posloupnost znaků, které představují bod kódu Unicode.  Tyto dvě různými formami trvat. Použití `\UNNNNNNNN` představující bod kódu Unicode ve formátu U + NNNNNNNN, kde NNNNNNNN je číslo s desetinnou čárkou kód osm číslic v šestnáctkové soustavě. Použití čtyř číslic `\uNNNN` představující bod kódu Unicode U + 0000NNNN ve formuláři.  
  
 V identifikátory a v literálech řetězců a znaků může používat univerzální názvy znaků. Univerzální název znaku nemůže používá k reprezentování náhradní bod kódu v rozsahu 0xD800-0xDFFF. Místo toho použít bod požadovaného kódu; kompilátor automaticky generuje všechny požadované zástupnými typy. Další omezení platí pro názvy univerzálních znaků, které lze použít v identifikátory. Další informace najdete v tématu [identifikátory](../cpp/identifiers-cpp.md) a [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md).  
  
 **Specifické pro Microsoft**  
  
 Kompilátor Visual C++ zpracovává znak v univerzálních znaků název literálu formuláři a Zaměnitelně. Můžete třeba deklarovat pomocí formuláře univerzálních znaků názvu identifikátor a použít v podobě literálu:  
  
```cpp  
auto \u30AD = 42; // \u30AD is 'キ'  
if (キ == 42) return true; // \u30AD and キ are the same to the compiler  
```  
  
 Formát rozšířené znaky do schránky Windows je specifické pro aplikaci nastavení národního prostředí. Vyjímání a vkládání do kódu z jiné aplikace tyto znaky může představovat neočekávaný znak kódování. To může způsobit chyby při analýze bez zjevné příčiny ve vašem kódu. Doporučujeme nastavit váš zdroj kódování souboru na znakovou stránku Unicode před vložením rozšířené znaky. Doporučujeme také použít editor IME nebo aplikace Mapa znaků ke generování rozšířené znaky.  
  
 **Specifické pro END Microsoft**  
  
### <a name="basic-execution-character-set"></a>Základní znaková sada spuštění  
 *Základní znakové sadě spuštění* a *základním provedení široká charakterová sada* obsahovat všechny znaky v základní zdrojové znakové sady a řídicí znaky, které představují oznámení, BACKSPACE, zalomení řádku a znak null. *Znaková sada spuštění* a *provádění široká charakterová sada* jsou nadmnožiny základní sady. Patří mezi ně definované implementací zdroj znaky mimo základní zdrojové znakové sady. Znaková sada spuštění má reprezentaci specifických pro národní prostředí.