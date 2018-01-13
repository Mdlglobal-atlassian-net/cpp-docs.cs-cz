---
title: "-ověření-charset (ověřit kompatibilní znaků) | Microsoft Docs"
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
- /validate-charset
- validate-charset
dev_langs: C++
helpviewer_keywords: /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7694eb94fe1b50d1892dab399b523a5b0e6deef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/Validate-Charset (ověřit kompatibilní znaky)
Ověří, zda zdrojový soubor text obsahuje pouze znaky reprezentovat jako UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/validate-charset[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít **/validate-charset** možnost ověřit, že zdrojový kód obsahuje jenom znaky, které může být reprezentován ve znaku zdroje nastavit a provádění znaková sada. Tato kontrola se povolí automaticky, když zadáte **/source-charset**, **/execution-charset**, nebo **/utf-8** – možnosti kompilátoru. Tato kontrola může explicitně zakázat zadáním **/ validate-charset -** možnost.  
  
 Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů kódování jak zjistit, pokud zdrojový soubor ve formátu Unicode kódovaného například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je kódované pomocí aktuální stránku kód uživatele, pokud jste zadali znaková stránka pomocí **/utf-8** nebo **/source-charset** možnost. Visual Studio můžete uložit vašeho zdrojového kódu C++ pomocí některé z několika kódování znaků. Informace o zdroje a provádění znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets2.md) v dokumentaci k jazyk. Seznam podporovaných identifikátory kódu stránky a znaková sada názvy, najdete v části [kódu stránky identifikátory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Visual Studio použije jako interní kódování znaků, které při převodu mezi znaková sada zdroje a znaková sada spuštění ve formátu UTF-8. Je-li znak ve zdrojovém souboru není možné vyjádřit v znaková sada spuštění, převodu znakové sady UTF-8 nahradí otazník '?' znak. **/Validate-charset** možnost způsobí, že kompilace nahlásit upozornění, pokud k ní dojde.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.  
  
3.  V **pokročilé možnosti**, přidejte **/validate-charset** možnost a zadejte upřednostňované kódování.  
  
4.  Zvolte **OK** uložte provedené změny.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Execution-Charset (nastavit provádění znaková sada)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/Source-Charset (nastavit zdroj znaková sada)](../../build/reference/source-charset-set-source-character-set.md)   
 [/UTF-8 (nastavit zdroj a spustitelný soubor znakových sad na UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)