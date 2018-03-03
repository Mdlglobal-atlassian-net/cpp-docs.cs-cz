---
title: "-provádění-charset (znaková sada spuštění sady) | Microsoft Docs"
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
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cfb315c0dece0edc6228f70ed3900be80543cc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="execution-charset-set-execution-character-set"></a>/Execution-Charset (nastavit provádění znaková sada)
Umožňuje zadat provádění znakovou sadu pro vaše spustitelný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/execution-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Arguments  
 **IANA_name**  
 Název znakové IANA definované sady.  
  
 **CPID**  
 Identifikátor kódu stránky.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít **/execution-charset** možnost zadat znaková sada spuštění. Znaková sada spuštění je kódování použité pro text programu, která není vstupní na fázi kompilace po všech předzpracování kroky. Znaková sada se používá pro interní reprezentaci všech řetězec nebo znak literály v zkompilovaný kód. Nastavení této možnosti určit znaková sada spuštění rozšířené použít zdrojové soubory obsahují znaky, které nejsou reprezentovat znaková sada základní spuštění. Můžete použít buď IANA nebo ISO znaková sada název nebo tečku (.), za nímž následuje identifikátor 3 až 5 číslic desetinných kódu stránky zadat znakovou sadu. Seznam podporovaných identifikátory kódu stránky a znaková sada názvy, najdete v části [kódu stránky identifikátory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů kódování jak zjistit, pokud zdrojový soubor ve formátu Unicode kódovaného například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je zakódován pomocí aktuálního uživatele znaková stránka uvedeno znaková sada název nebo kódu stránky pomocí **/source-charset** možnost nebo **/utf-8** možnost. Visual Studio můžete uložit vašeho zdrojového kódu C++ pomocí některé z několika kódování znaků. Informace o zdroje a provádění znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets2.md) v dokumentaci k jazyk.  
  
 Pokud chcete nastavit zdroj znakovou sadu a znaková sada spuštění na UTF-8, můžete použít **/utf-8** – možnost kompilátoru jako zástupce. Je ekvivalentní **/source-charset:utf-8 /execution-charset:utf-8** na příkazovém řádku. Některý z těchto možností také umožňuje **/validate-charset** možnost ve výchozím nastavení.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.  
  
3.  V **pokročilé možnosti**, přidejte **/execution-charset** možnost a zadejte upřednostňované kódování.  
  
4.  Zvolte **OK** uložte provedené změny.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Source-Charset (nastavit zdroj znaková sada)](../../build/reference/source-charset-set-source-character-set.md)   
 [/UTF-8 (nastavit zdroj a spustitelný soubor znakových sad na UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/Validate-Charset (ověřit kompatibilní znaky)](../../build/reference/validate-charset-validate-for-compatible-characters.md)