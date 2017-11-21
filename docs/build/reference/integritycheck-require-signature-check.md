---
title: "-INTEGRITYCHECK (vyžadují Kontrola podpisu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5623d822ed02439cdec5dd92cbb687eebad6acdf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (povinná kontrola podpisu)
Určuje, že digitální podpis binární Image se musí kontrolovat v okamžiku načtení.  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení **/INTEGRITYCHECK** je vypnutý.  
  
 **/INTEGRITYCHECK** možnost nastaví – v záhlaví PE souboru DLL nebo spustitelný soubor – příznak pro správce paměti vyhledávat digitální podpis, aby bylo možné načíst obrázek v systému Windows. Tato možnost musí být nastavena pro 32bitové i 64bitové knihovny DLL, které implementují kód režimu jádra načtený některými funkcemi systému Windows, a je doporučena pro všechny ovladače zařízení v systémech Windows Vista, [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08](../../build/reference/includes/winsvr08_md.md)] a [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]. Verze Windows starší než Windows Vista Ignorovat tento příznak. Další informace najdete v tématu [vynutit integritu podepisování z přenosné spustitelný soubor (PE) soubory](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **příkazového řádku** stránku vlastností.  
  
5.  V **další možnosti**, zadejte `/INTEGRITYCHECK` nebo `/INTEGRITYCHECK:NO`.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [Vynucené soubory Integrity podepisování z přenosné spustitelný soubor (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Návod pro podpis kódu režimu jádra](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [Knihovny DLL Applnit v systému Windows 7 a Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)