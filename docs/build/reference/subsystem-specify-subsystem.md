---
title: -SUBSYSTEM (zadat subsystém) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70d6f047cf18b8b768d40533e2acc6cb2f649327
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379000"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Zadat subsystém)
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT_APPLICATION  
 Aplikace, která běží v prostředí spouštění systému Windows. Další informace o spouštění aplikací najdete v tématu [o BCD](http://msdn.microsoft.com/library/windows/desktop/aa362639).  
  
 KONZOLA  
 Aplikace Win32 režim znaků. Operační systém poskytuje konzoli pro konzolové aplikace. Pokud `main` nebo `wmain` je definována pro nativní kód `int main(array<String ^> ^)` je definována pro spravovaný kód, nebo zcela sestavení aplikace pomocí `/clr:safe`, KONZOLA je výchozí hodnota.  
  
 Extensible Firmware Interface  
 EFI_ * subsystémy. V tématu Specifikace EFI Další informace. Například najdete na webu společnosti Intel. Minimální verze verze a výchozím nastavení je 1.0.  
  
 NATIVNÍ  
 Ovladače režimu jádra pro systém Windows NT. Tato možnost je obvykle vyhrazený pro součásti systému Windows. Pokud [/DRIVER:WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md) je zadána výchozí hodnota je NATIVNÍ.  
  
 POSIX  
 Aplikaci, která pracuje s subsystému POSIX v systému Windows NT.  
  
 WINDOWS  
 Aplikace nevyžaduje konzoly, pravděpodobně, protože se tím vytvoří vlastní windows pro interakci s uživatelem. Pokud `WinMain` nebo `wWinMain` je definována pro nativní kód, nebo `WinMain(HISTANCE *, HINSTANCE *, char *, int)` nebo `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` je definována pro spravovaný kód, WINDOWS, je výchozí.  
  
 `Major` a `minor` (volitelné)  
 Zadejte minimální požadovaná verze subsystému. Argumenty jsou desítková číslice v rozsahu 0 až 65 535. V části poznámky Další informace. Neexistují žádné horní rozsah čísel verzí.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /SUBSYSTEM Určuje prostředí pro spustitelný soubor.  
  
 Volba subsystému ovlivní symbol vstupního bodu (nebo funkce vstupního bodu), bude vyberete linkeru.  
  
 Volitelné minimální a výchozí `major` a `minor` čísla verzí pro subsystémy jsou následující.  
  
|Subsystém|Minimální|Výchozí|  
|---------------|-------------|-------------|  
|BOOT_APPLICATION|1.0|1.0|  
|KONZOLA|5.01 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6.00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|WINDOWS|5.01 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6.00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|NATIVNÍ (s ovladače: WDM)|1.00 (x 86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|1.00 (x 86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|  
|NATIVNÍ (bez /DRIVER:WDM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|POSIX|1.0|19.90|  
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Vyberte složku, Linkeru.  
  
3.  Vyberte **systému** stránku vlastností.  
  
4.  Změnit `SubSystem` vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)