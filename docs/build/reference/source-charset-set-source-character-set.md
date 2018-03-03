---
title: "-Zdroj-charset (sada zdroj znaková sada) | Microsoft Docs"
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
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4aa81ba41587a183aca921177a62a45229810f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="source-charset-set-source-character-set"></a>/Source-Charset (nastavit zdroj znaková sada)
Umožňuje zadat zdroj znakovou sadu pro vaše spustitelný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/source-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Arguments  
 **IANA_name**  
 Název znakové IANA definované sady.  
  
 **CPID**  
 Identifikátor kódu stránky jako s desetinným číslem.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít **/source-charset** možnost zadat rozšířené zdrojová znaková sada použít zdrojové soubory obsahují znaky, které nejsou reprezentovány ve znakové sadě základní zdroj. Znaková sada zdroj je kódování použité k interpretaci zdrojový text vašeho programu do interního vyjádření používá jako vstup pro předběžného zpracování fáze před kompilace. Interního vyjádření je potom převedou do znaková sada spuštění pro uložení řetězce a znak hodnot ve spustitelném souboru. Můžete použít buď IANA nebo ISO znaková sada název nebo tečku (.), za nímž následuje identifikátor 3 až 5 číslic desetinných kódu stránky zadat znakovou sadu. Seznam podporovaných identifikátory kódu stránky a znaková sada názvy, najdete v části [kódu stránky identifikátory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů kódování jak zjistit, pokud zdrojový soubor ve formátu Unicode kódovaného například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je kódované pomocí aktuální stránku kód uživatele, pokud nezadáte znaková sada stránku název nebo kódu pomocí **/source-charset** možnost. Visual Studio můžete uložit vašeho zdrojového kódu C++ pomocí některé z několika kódování znaků. Další informace o zdroje a provádění znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets2.md) v dokumentaci k jazyk.  
  
 Znaková sada zdroje, které zadáte musí být mapována 7 rozšířené znaky ASCII stejné body kódu ve znakové sadě, nebo jsou pravděpodobností mnoho chyb kompilace. Váš zdroj znakovou sadu musí být také lze mapovat na rozšířenou sadu Kódovat pomocí znakové sady UTF-8 znaků Unicode. Znaky, které nejsou kódovat ve formátu UTF-8 jsou reprezentované pomocí substitute konkrétní implementace. Kompilátor Microsoft používá otazník pro tyto znaky.  
  
 Pokud chcete nastavit zdroj znakovou sadu a znaková sada spuštění na UTF-8, můžete použít **/utf-8** – možnost kompilátoru jako zástupce. Je ekvivalentní **/source-charset:utf-8 /execution-charset:utf-8** na příkazovém řádku. Některý z těchto možností také umožňuje **/validate-charset** možnost ve výchozím nastavení.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.  
  
3.  V **pokročilé možnosti**, přidejte **/source-charset** možnost a zadejte upřednostňované kódování.  
  
4.  Zvolte **OK** uložte provedené změny.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Execution-Charset (nastavit provádění znaková sada)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/UTF-8 (nastavit zdroj a spustitelný soubor znakových sad na UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/Validate-Charset (ověřit kompatibilní znaky)](../../build/reference/validate-charset-validate-for-compatible-characters.md)