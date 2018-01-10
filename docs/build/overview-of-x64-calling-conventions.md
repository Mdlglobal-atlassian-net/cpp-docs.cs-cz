---
title: "Přehled x64 konvence volání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ac42eb934692fb9eaecf345b75e7544e7078f07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-x64-calling-conventions"></a>Přehled konvencí volání v prostředí x64
Dvě důležité rozdíly mezi x86 a [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] jsou schopnosti adresování 64-bit a plochá sada 16 64-bit registrů pro obecné použití. Daná rozšířeného registru, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] používá [__fastcall](../cpp/fastcall.md) volání konvence a založených RISC model zpracování výjimek. `__fastcall` Konvence používá registry pro první čtyři argumenty a rámce zásobníku předat další argumenty.  
  
 Následující možnost kompilátoru pomůže vám při optimalizaci aplikace pro [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]:  
  
-   [/ favor (optimalizace pro konkrétní architekturu)](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## <a name="calling-convention"></a>Konvence volání  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] Binární rozhraní aplikace (ABI) používá konvence volání rychlého volání čtyři zaregistrovat ve výchozím nastavení. V zásobníku volání je jako stínové úložiště pro volané uložit tyto registry přiděleno místo. Je mezi argumenty pro volání funkce a zaregistruje se používá pro tyto argumenty striktní souvislosti. Některý argument, který se nevejde do 8 bajtů, nebo není 1, 2, 4 nebo 8 bajtů, musí být předán odkazem. Neexistuje žádný pokus o rozloženy více registry jeden argument. X87 zásobník registru se nepoužívá. Může být používán volaného, ale je třeba zvážit volatile napříč volání funkcí. Plovoucí desetinná čárka všechny operace se provádějí pomocí 16 XMM registrů. Celé číslo argumenty jsou předány v registrech RCX, RDX, R8 a R9. Číslo s plovoucí desetinnou argumenty se předávají v XMM0L, XMM1L, XMM2L a XMM3L. 16 bajtů argumenty jsou předávány odkazem. Předávání parametrů je podrobně popsány v [předání parametru](../build/parameter-passing.md). Kromě těchto registry RAX R10, R11, XMM4 a XMM5 závislé jsou považovány za volatile. Všechny ostatní registry jsou stálé. Využití registrů je podrobně popsaná v [zaregistrovat využití](../build/register-usage.md) a [uložit zaregistruje volající/volaný](../build/caller-callee-saved-registers.md).  
  
 Volající zodpovídá za přidělování místa pro parametry volaného a přidělíte vždy dost místa pro uložení čtyři parametry registru, i když volaného neberou v tolika parametry. Tato funkce zjednodušuje podpora Neprototypové funkce jazyka C a vararg C/C++ funkce. Pro vararg nebo neprototypové funkce, všechny plovoucí desetinné čárky hodnoty musí být duplicitní v odpovídajícím pro obecné účely registrace. Žádné parametry nad rámec první čtyři musí být uložen v zásobníku výše stínové úložiště pro první čtyři, před voláním. Vararg – funkce podrobnosti naleznete v [vararg](../build/varargs.md). Neprototypové funkce informace je podrobně popsaná v [Neprototypové funkce](../build/unprototyped-functions.md).  
  
## <a name="alignment"></a>Zarovnání  
 Většina struktury je zarovnán jejich přirozené zarovnání. Primární výjimky jsou ukazatel zásobníku a `malloc` nebo `alloca` paměti, které odpovídají na 16 bajtů za účelem zlepšení výkonu. Zarovnání výše 16 bajtů je třeba provést ručně, ale protože 16 bajtů je běžná velikost zarovnání pro XMM operace, tento postup měl fungovat pro většinu kódu. Další informace o struktuře rozložení a zarovnání najdete v části [typy a úložiště](../build/types-and-storage.md). Informace o rozložení zásobníku najdete v tématu [použití zásobníku](../build/stack-usage.md).  
  
## <a name="unwindability"></a>Funkcionalita unwind  
 Funkce listu jsou funkce, které se nemění žádné nezávislé registry. Funkce mimo úroveň listu může změnit stálé konfigurace, například volání funkce a přidělování další prostor v zásobníku pro místní proměnné. Chcete-li obnovit nezávislé registry, když je výjimka ošetřena, musí být opatřena statických dat, který popisuje, jak správně unwind funkci na libovolný instrukce poznámkou funkce mimo úroveň listu. Tato data jsou ukládána jako *pdata*, nebo postup data, která naopak odkazuje na *xdata*, zpracování dat výjimek. Xdata unwinding informacemi a může odkazovat na další pdata nebo funkce obslužné rutiny výjimky. Prology a epilogu funkce jsou vysoce omezenou tak, aby mohly být správně popsány v xdata. Ukazatel zásobníku musí být zarovnána na 16 bajtů v libovolné oblasti kód, který není součástí epilogu nebo prologu, s výjimkou v rámci funkcí listu. Funkce listu můžete odděleny jednoduše tak, že simuluje vrátit, takže pdata a xdata není potřeba. Podrobnosti o správné struktuře Prology funkce a epilogu funkce najdete v tématu [Prolog a Epilog](../build/prolog-and-epilog.md). Další informace o zpracování výjimek a zpracování výjimek a unwinding pdata a xdata najdete v tématu [zpracování výjimek (x64)](../build/exception-handling-x64.md).  
  
## <a name="see-also"></a>Viz také  
 [x64 – softwarové konvence](../build/x64-software-conventions.md)