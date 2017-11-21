---
title: "Čistý a ověřitelný kód (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ec68a6179cd74020638aa895028942bc76e21f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pure-and-verifiable-code-ccli"></a>Čistý a ověřitelný kód (C++/CLI)
Pro programování v rozhraní .NET podporuje aplikace Visual C++ vytváření tří různých typů komponent a aplikací: smíšené, čisté a ověřitelné. Všechny tři jsou k dispozici prostřednictvím [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o ověřitelných sestaveních najdete v tématu:  
  
-   [Smíšené, čisté a ověřitelné porovnání funkcí (C + +/ CLI)](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [Postupy: přechod na/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [Postupy: Vytvoření ověřitelných projektů jazyka C++ (C + +/ CLI)](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [Postupy: migrace na/CLR: safe (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [Použití ověřitelných sestavení se serverem SQL Server (C + +/ CLI)](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [Osvědčené postupy zabezpečení](../security/security-best-practices-for-cpp.md)  
  
-   [Převod projektů ze smíšeného režimu do čistého IL](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## <a name="mixed-clr"></a>Smíšená (/ clr)  
 Smíšená sestavení (Kompilovat s **/CLR**), obsahuje obě nespravované a spravované části, což jim umožňuje používat funkce rozhraní .NET, ale stále obsahuje nespravovaný kód. To umožňuje aplikací a součástí aktualizovat bez nutnosti, že se celý projekt přepsaná použití funkcí rozhraní .NET. Pomocí Visual C++ kombinovat spravovanými a nespravovanými kódu tímto způsobem se nazývá zprostředkovatele komunikace C++. Další informace najdete v tématu [Mixed (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) a [nativní a interoperabilitě .NET](../dotnet/native-and-dotnet-interoperability.md).  
  
## <a name="pure-clrpure"></a>Čistý (/ clr: pure)  
 Čistá sestavení (Kompilovat s **/CLR: pure**) může obsahovat i nativní a spravované datové typy, ale pouze spravované funkce. Stejně jako smíšená sestavení, čistá sestavení umožňují spolupráci s nativní knihovny DLL pomocí P/Invoke (viz [pomocí explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)), ale nejsou k dispozici funkce interoperability C++. Kromě toho, čistá sestavení nelze exportovat funkce, které jsou volány z nativní funkce, protože vstupní body v čistém sestavení používají [__clrcall](../cpp/clrcall.md) konvence volání.  
  
### <a name="advantages-of-clrpure"></a>Výhody/clr: pure  
  
-   Vyšší výkon: Jelikož čistá sestavení obsahují pouze jazyk MSIL, nejsou použity žádné nativní funkce, a proto není zapotřebí žádných přechodů mezi spravovaným a nespravovaným kódem. (Volání funkce prostřednictvím P/Invoke jsou výjimkou tohoto pravidla).  
  
-   Sledování domény aplikace: Spravované funkce a datové typy CLR existují uvnitř domén aplikací (`Application Domains`), což ovlivňuje jejich viditelnost a přístupnost. Čistá sestavení jsou podporující domain (__declspec ([appdomain](../cpp/appdomain.md)) je pro každý typ implicitní), přístup k jejich typy a funkce ze součásti rozhraní .NET je snazší a bezpečnější. V důsledku toho čistá sestavení spolupracovat snadněji s ostatními součástmi .NET než smíšená sestavení.  
  
-   Načítání mimo disk: Čistá sestavení lze načíst uvnitř paměti a lze je dokonce vysílat datovým proudem. To je nezbytné pro použití sestavení .NET jako uložené procedury. To se liší od smíšených sestavení, které načítání mechanismy, musí existovat na disku, aby bylo možné provést z důvodu závislosti na systému Windows.  
  
-   Reflexe: Nelze provádět reflexi pro smíšené spustitelné soubory, zatímco čistá sestavení poskytují plnou podporu reflexe. Další informace najdete v tématu [reflexe (C + +/ CLI)](../dotnet/reflection-cpp-cli.md).  
  
-   Ovladatelnost hostitele: Jelikož čistá sestavení obsahují pouze jazyk MSIL, chovají se při použití v aplikacích, které jsou hostiteli pro modul CLR a upravují jeho výchozí chování, předvídatelněji a flexibilněji než smíšená sestavení.  
  
### <a name="limitations-of-clrpure"></a>Omezení/CLR: pure  
 Tato část zahrnuje funkce není aktuálně podporovaná **/CLR: pure**.  
  
-   Čistá sestavení nelze volat z nespravovaných funkcí. Čistá sestavení nelze proto implementovat rozhraní modelu COM nebo vystavit nativní zpětná volání. Čistá sestavení nelze exportovat funkce prostřednictvím __declspec(dllexport) nebo. DEF soubory. Také funkce deklarovat s \__clrcall konvence nelze importovat prostřednictvím \__declspec(dllimport). Funkce v nativní modul může volat z čistá sestavení, ale čistá sestavení nelze vystavit nativní zpětné volání funkce, takže vystavení funkce v čistá sestavení je třeba provést prostřednictvím spravované funkcí v smíšená sestavení. Najdete v části [postupy: přechod na/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md) Další informace.  
  
-   Režim čisté kompilace nepodporuje v jazyce Visual C++ knihovny ATL a MFC.  
  
-   Čisté moduly .netmodule nejsou podporovány jako vstup do linkeru jazyka Visual C++. Ale přijímat čisté soubory .obj jsou linkeru a soubory .obj obsahovat nadmnožinou informace obsažené v netmodules. V tématu [.netmodule soubory jako vstup Linkeru](../build/reference/netmodule-files-as-linker-input.md) Další informace.  
  
-   Podpora kompilátoru modelu COM (#import) není podporována, protože by to vytvořilo nespravované instrukce do čistého sestavení.  
  
-   Číslo s plovoucí desetinnou nejsou upravitelné pro čistá sestavení možnosti pro zarovnání a zpracování výjimek. V důsledku toho nelze použít __declspec(align). To vykreslí některé soubory hlaviček, jako je například fpieee.h, není kompatibilní s volbou/CLR: pure.  
  
-   Funkce GetLastError v PSDK může poskytnout nedefinované chování, když kompilujete s **/CLR: pure**.  
  
## <a name="verifiable-clrsafe"></a>Ověřitelná (/ CLR: safe)  
 **/CLR: safe** generuje ověřitelná sestavení, jako jsou napsané v jazyce Visual Basic a C#, vyhovující požadavků, které modul CLR (CLR) Chcete-li zaručit, že kód není porušují aktuální – možnost kompilátoru nastavení zabezpečení. Například pokud nastavení zabezpečení zakazují komponentě zápis na disk, modul CLR může určit Pokud ověřitelný součást splňuje tato kritéria před provedením kód. Neexistuje žádná podpora CRT pro ověřitelná sestavení. (CRT – podpora je k dispozici pro čistá sestavení prostřednictvím čistá MSIL verzi C Runtime library).  
  
 Ověřitelná sestavení nabízejí tyto výhody oproti čisté a smíšená sestavení:  
  
-   Zvýšení zabezpečení.  
  
-   Některé situace vyžadují ho (například součásti SQL).  
  
-   Budoucích verzích systému Windows bude stále vyžadují součásti a aplikace ověřené.  
  
 Jednou z nevýhod je, že funkce interoperability C++ nejsou k dispozici. Ověřitelná sestavení nemůže obsahovat žádné nespravované funkce nebo nativní datové typy, i když nejsou odkazuje spravovaného kódu.  
  
 Bez ohledu na použití slovo "safe", kompilace aplikace s **/CLR: safe** neznamená zde nejsou žádné chyby; právě znamená, že modulu CLR můžete ověřit nastavení zabezpečení v době běhu.  
  
 Bez ohledu na typ sestavení volání ze spravovaných sestavení do nativních knihoven DLL prostřednictvím P/Invoke bude kompilovat, ale může dojít k selhání za běhu v závislosti na nastavení zabezpečení.  
  
> [!NOTE]
>  Existuje jedna situace kódování, která bude úspěšně zkompilována, ale povede k neověřitelnému sestavení: volání virtuální funkce instancí objektu pomocí operátoru pro rozlišení oboru.  Příklad: `MyObj -> A::VirtualFunction();`.  
  
## <a name="see-also"></a>Viz také  
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)