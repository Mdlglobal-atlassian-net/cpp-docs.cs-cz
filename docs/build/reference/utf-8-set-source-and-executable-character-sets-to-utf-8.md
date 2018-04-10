---
title: znakové sady utf - 8 (nastavit zdroj a spustitelný soubor znakových sad na UTF-8) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /utf-8
dev_langs:
- C++
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 592cba779113a6658b40d0dc3f855f53fa3d170c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/UTF-8 (nastavit zdroj a spustitelný soubor znakových sad na UTF-8)
Určuje, jak zdrojová znaková sada a znaková sada spuštění jako UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/utf-8  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít **/utf-8** možnost zadat zdroj a provádění znakové sady jako kódované pomocí znakové sady UTF-8. Je ekvivalentní **/source-charset:utf-8 /execution-charset:utf-8** na příkazovém řádku. Některý z těchto možností také umožňuje **/validate-charset** možnost ve výchozím nastavení. Seznam podporovaných identifikátory kódu stránky a znaková sada názvy, najdete v části [kódu stránky identifikátory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů kódování jak zjistit, pokud zdrojový soubor ve formátu Unicode kódovaného například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je kódované pomocí aktuální stránku kód uživatele, pokud jste zadali znaková stránka pomocí **/utf-8** nebo **/source-charset** možnost. Visual Studio můžete uložit vašeho zdrojového kódu C++ pomocí některé z několika kódování znaků. Informace o zdroje a provádění znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets2.md) v dokumentaci k jazyk.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.  
  
3.  V **pokročilé možnosti**, přidejte **/utf-8** možnost a zadejte upřednostňované kódování.  
  
4.  Zvolte **OK** uložte provedené změny.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Execution-Charset (nastavit provádění znaková sada)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/Source-Charset (nastavit zdroj znaková sada)](../../build/reference/source-charset-set-source-character-set.md)   
 [/Validate-Charset (ověřit kompatibilní znaky)](../../build/reference/validate-charset-validate-for-compatible-characters.md)