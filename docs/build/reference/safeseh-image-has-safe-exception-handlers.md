---
title: -SAFESEH (bitová kopie má bezpečné obslužné rutiny výjimek) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54d13e6922650f0193d4bbc3469d4acf25904234
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (Bitová kopie má bezpečné obslužné rutiny výjimek)
```  
/SAFESEH[:NO]  
```  
  
 Když **/SAFESEH** není zadaný, linkeru pouze vytvoří bitovou kopii, pokud ho také vytvoření tabulky obslužné rutiny bezpečné výjimek obrázku. Tato tabulka určuje, které obslužné rutiny výjimek jsou v operačním systému pro bitovou kopii platné.  
  
 **/ SAFESEH** je platný pouze při propojení pro x86 cíle. **/ SAFESEH** není podporována pro platformy, které již mají obslužné rutiny výjimek uvedené. Například pro architektury [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] a ARM jsou všechny obslužné rutiny výjimek poznamenány ve strukturách PDATA. ML64.exe podporuje přidávání poznámek, které generují informace SEH (XDATA a PDATA) do bitové kopie a umožňují tak rozbalování pomocí funkcí ml64. V tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) Další informace.  
  
 Pokud **/SAFESEH** není zadán, linkeru vytvoří bitovou kopii s tabulkou obslužných rutin výjimek bezpečné, pokud všechny moduly, které jsou kompatibilní s funkcí bezpečné zpracování výjimek. Pokud kterýkoli z modulů nebyl s funkcí bezpečného zpracování výjimek kompatibilní, výsledná bitová kopie nebude tabulku bezpečných obslužných rutin výjimek obsahovat. Pokud [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) určuje WINDOWSCE nebo jeden z těchto EFI_ * možností linkeru nebude pokoušet vytvořit bitovou kopii s tabulkou obslužných rutin výjimek bezpečné, stejně jako ani jeden z těchto subsystémy můžete provádět pomocí informací.  
  
 Pokud **/SAFESEH:NO** není zadaný, linkeru nebude vytvořit bitovou kopii s tabulkou obslužných rutin výjimek bezpečné, i když jsou kompatibilní s bezpečné zpracování funkce výjimek všechny moduly.  
  
 Nejčastějším důvodem, proč linker nedokáže vytvořit bitovou kopii, je nekompatibilita jednoho nebo více vstupních souborů (modulů) linkeru s funkcí bezpečného zpracování výjimek. Častým důvodem, proč není modul kompatibilní s bezpečnými obslužnými rutinami výjimek, je, že byl vytvořen kompilátorem z předchozí verze jazyka Visual C++.  
  
 Můžete také registrovat funkce jako obslužná rutina strukturovaného výjimek pomocí [. SAFESEH](../../assembler/masm/dot-safeseh.md).  
  
 U existujícího binárního souboru nelze označit, že obsahuje bezpečné obslužné rutiny výjimek (nebo neobsahuje žádné obslužné rutiny). Informace o bezpečném zpracování výjimek musí být přidány během sestavování.  
  
 Schopnost linkeru sestavit tabulku bezpečných obslužných rutin výjimek závisí na tom, zda aplikace používá knihovnu runtime jazyka C. Pokud jste s [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) a chcete tabulku obslužné rutiny výjimek bezpečné, budete muset zadat struktury konfigurace zatížení (například lze nalézt v loadcfg.c CRT zdrojový soubor) obsahující všechny položky, které jsou definované pro Visual C++. Příklad:  
  
```  
#include <windows.h>  
extern DWORD_PTR __security_cookie;  /* /GS security cookie */  
  
/*  
 * The following two names are automatically created by the linker for any  
 * image that has the safe exception table present.  
*/  
  
extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */  
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is  
                                           the count of table entries */  
typedef struct {  
    DWORD       Size;  
    DWORD       TimeDateStamp;  
    WORD        MajorVersion;  
    WORD        MinorVersion;  
    DWORD       GlobalFlagsClear;  
    DWORD       GlobalFlagsSet;  
    DWORD       CriticalSectionDefaultTimeout;  
    DWORD       DeCommitFreeBlockThreshold;  
    DWORD       DeCommitTotalFreeThreshold;  
    DWORD       LockPrefixTable;            // VA  
    DWORD       MaximumAllocationSize;  
    DWORD       VirtualMemoryThreshold;  
    DWORD       ProcessHeapFlags;  
    DWORD       ProcessAffinityMask;  
    WORD        CSDVersion;  
    WORD        Reserved1;  
    DWORD       EditList;                   // VA  
    DWORD_PTR   *SecurityCookie;  
    PVOID       *SEHandlerTable;  
    DWORD       SEHandlerCount;  
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;  
  
const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {  
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    &__security_cookie,  
    __safe_se_handler_table,  
    (DWORD)(DWORD_PTR) &__safe_se_handler_count  
};  
```  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)