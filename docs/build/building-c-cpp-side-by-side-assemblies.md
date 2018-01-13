---
title: "Vytváření sestavení C/C++-souběžného | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c54f0e3b8bceff3daa92ecb3e0ee46d7fbeb666
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="building-cc-side-by-side-assemblies"></a>Sestavení souběžných sestavení C/C++
A [souběžně sdílená sestavení](http://msdn.microsoft.com/library/windows/desktop/ff951640) je kolekce prostředků – skupinu knihovny DLL, třídy windows, serverů modelu COM, knihovny typů nebo rozhraní – k dispozici pro aplikace pro použití v době běhu. Primární výhodou opětovné vytvoření balíčku knihovny DLL v sestavení je, že více verzí sestavení je použít v aplikacích ve stejnou dobu a je možné sestavení aktuálně nainstalována v případě vydání aktualizace.  
  
 Aplikace Visual C++ může používat jednoho nebo několika knihovny DLL v různých částí aplikace. Za běhu knihovny DLL jsou načtena do procesu hlavní a požadované kód se spustí. Aplikace závisí na operačním systému najít požadované knihovny DLL, pochopit, co další závislé knihovny DLL mají načíst a pak je můžete načíst společně s požadovanou knihovnu DLL. Ve verzích operačních systémů Windows starších než Windows XP, Windows Server 2003 a Windows Vista, zavaděč operačního systému hledá závislé knihovny DLL v místní složce aplikace nebo jiné složky, které jsou definované na cestě k systému souborů. V systému Windows XP, Windows Server 2003 a Windows Vista, zavaděč operačního systému můžete taky vyhledat závislé knihovny DLL pomocí [manifest](http://msdn.microsoft.com/library/windows/desktop/aa375365) soubor a vyhledejte souběžně sdílená sestavení, které obsahují tyto knihovny DLL.  
  
 Ve výchozím nastavení, když je sestavena knihovny DLL pomocí sady Visual Studio, má [manifest aplikace](http://msdn.microsoft.com/library/windows/desktop/aa374191) vložených jako RT_MANIFEST prostředek s ID rovna 2. Stejně jako u spustitelného souboru tento manifest popisuje závislosti této knihovny DLL na ostatních sestavení. To předpokládá, že je DLL není součástí souběžně sdílená sestavení a aplikace, které jsou závislé na této knihovny DLL nebudete používat manifest aplikace načíst, ale místo toho spoléhají na zavaděč operačního systému k vyhledání této knihovny DLL na cestě k systému souborů.  
  
> [!NOTE]
>  Je důležité pro knihovnu DLL, kterou používá manifest aplikace tak, aby měl manifest vložený jako prostředek s ID rovna 2. Pokud načtení knihovny DLL dynamicky za běhu (například pomocí [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175) funkce), operační systém načte závislá sestavení zadané v manifestu knihovnu DLL. Při nastavení není kontrolován manifest externí aplikace pro knihovny DLL `LoadLibrary` volání. Pokud není vložená manifest, zavaděč můžou snažit načítání nesprávné verze sestavení nebo nepodaří najít k vyhledání závislá sestavení.  
  
 Jeden nebo několik související s knihovny DLL může být znovu zabalené do souběžně sdílená sestavení s odpovídající [manifest sestavení](http://msdn.microsoft.com/library/windows/desktop/aa374219), který popisuje soubory, které tvoří na jiné-souběžného sestavení, jakož i závislost sestavení sestavení.  
  
> [!NOTE]
>  Pokud sestavení obsahuje jednu knihovnu DLL, se doporučuje pro vložení manifestu sestavení do této knihovny DLL jako prostředek s ID rovno 1 a pojmenujte privátní sestavení má stejný název jako knihovnu DLL. Například pokud je název souboru DLL mylibrary.dll, hodnota atributu název se používá v \<assemblyIdentity > element manifestu je také možné Moje knihovna. V některých případech, když má příponu než DLL knihovny (například projektu ovládací prvky MFC ActiveX vytvoří knihovnu .ocx) je možné vytvořit manifest externí sestavení. Název sestavení a jeho manifestu v takovém případě musí být jiný než název knihovny DLL (například MyAssembly, MyAssembly.manifest a mylibrary.ocx). Ale stále doporučujeme přejmenovat tyto knihovny extension.dll a vložení manifestu jako prostředek snížit náklady na budoucí údržbu tohoto sestavení. Další informace o tom, jak operační systém vyhledá soukromá sestavení najdete v tématu [pořadí hledání sestavení](http://msdn.microsoft.com/library/windows/desktop/aa374224).  
  
 Tato změna může povolit nasazení knihoven DLL odpovídající jako [privátní sestavení](http://msdn.microsoft.com/library/windows/desktop/aa370850) v místní složce aplikace nebo jako [sdílené sestavení](http://msdn.microsoft.com/library/windows/desktop/aa371839) v mezipaměti WinSxS sestavení. Máte několik kroků za účelem dosažení správný modul runtime chování této nové sestavení; jsou popsány v [pokyny pro vytváření souběžně sdílená sestavení](http://msdn.microsoft.com/library/windows/desktop/aa375155). Po sestavení správně vytvořena můžete nasadit jako buď sdílené nebo privátní sestavení společně s aplikací, která na něm závisí. Když instalujete souběžně sdílená sestavení jako sdílené sestavení, mohou být buď postupujte podle pokynů uvedených v [instalaci Win32 sestavení pro sdílení vedle sebe na systému Windows XP](http://msdn.microsoft.com/library/windows/desktop/aa369532) nebo použijte [slučovací moduly](http://msdn.microsoft.com/library/windows/desktop/aa369820). Když instalujete souběžně sdílená sestavení jako privátní sestavení, může právě zkopírujete odpovídající knihovny DLL, prostředky a sestavení manifest jako součást procesu instalace do místní složky aplikace na cílovém počítači, zajistíte, že může být toto sestavení nalezena. zavaděč za běhu (viz [pořadí hledání sestavení](http://msdn.microsoft.com/library/windows/desktop/aa374224)). Dalším způsobem je použít [Instalační služby systému Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688) a postupujte podle pokynů uvedených v [instalaci Win32 sestavení pro soukromé použití aplikace v systému Windows XP](http://msdn.microsoft.com/library/windows/desktop/aa369534).  
  
## <a name="see-also"></a>Viz také  
 [Příklady nasazení](../ide/deployment-examples.md)   
 [Sestavení C/C++ izolovaných aplikací](../build/building-c-cpp-isolated-applications.md)   
 [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)