---
title: Přehled x64 konvence volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e70f4017cb31fcc76b1cf3ef2a77d3a28e31bd28
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707990"
---
# <a name="overview-of-x64-calling-conventions"></a>Přehled konvencí volání v prostředí x64

Jsou dva důležité rozdíly mezi x86 a x64 schopnosti adresování 64bitovým kompilátorem a ploché sady 16 64-bit zaregistruje pro obecné použití. Zadané sady rozšířené registr, používá x64 [__fastcall](../cpp/fastcall.md) volání vytváření názvů a jako model založený na RISC zpracování výjimek. `__fastcall` Konvence používá registry pro prvních čtyř argumentů a rámce zásobníku pro předání dalších argumentů.

Následující možnost kompilátoru umožňuje optimalizovat aplikaci pro x64:

- [/favor (optimalizace pro konkrétní architekturu)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="calling-convention"></a>Konvence volání

X64 binární rozhraní aplikace (ABI) používá konvence volání rychlého volání čtyři registr ve výchozím nastavení. Jako úložiště stínové pro volané uložte tyto registry není přiděleno místo v zásobníku volání. Existuje striktní shoda mezi argumenty pro volání funkce a registry použité pro tyto argumenty. Jakýkoliv argument, který se nevejde do 8 bajtů nebo není 1, 2, 4 nebo 8 bajtů, musejí být předány podle odkazu. Neexistuje žádný pokus o jeden argument rozloženy více registrů. X87 zásobník registru se nepoužívá. Může být používán volaný, ale musíte vzít v úvahu volatile ve volání funkce. S plovoucí desetinnou čárkou všechny operace se provádějí pomocí 16 registry XMM. Celočíselné argumenty jsou předány v registrech RCX, RDX, R8 a R9. Plovoucí desetinná čárka, že jsou argumenty předávány v XMM0L, XMM1L, XMM2L a XMM3L. 16 bajtů argumenty jsou předány podle odkazu. Předávání parametrů je podrobně popsány v [předávání parametru](../build/parameter-passing.md). Kromě těchto registrů RAX, R10, R11, XMM4 a XMM5 považují volatile. Všechny ostatní registry jsou není typu volatile. Využití registrů je podrobně popsáno v [zaregistrovat využití](../build/register-usage.md) a [volající/volaný – uloží zaregistruje](../build/caller-callee-saved-registers.md).

Volající zodpovídá za přidělování prostoru pro parametry volaného a musí vždy přidělit dostatek místa pro uložení čtyři parametry registru, i v případě, že volaný nepřijímá daný počet parametrů. Tato funkce usnadňuje podporu Neprototypové funkce jazyka C a C/C++ funkce vararg. Pro funkce vararg nebo unprototyped plovoucí čárky hodnoty musí být duplicitní do odpovídajícího registru pro obecné účely. Žádné parametry kromě první čtyři musí být uložen v zásobníku nahoře stínové úložiště pro první čtyři před voláním. Najdete podrobnosti funkce vararg v [Varargs](../build/varargs.md). Neprototypové funkce informace je podrobně popsaná v [Neprototypové funkce](../build/unprototyped-functions.md).

## <a name="alignment"></a>Zarovnání

Většina struktury jsou zarovnány na jejich přirozené zarovnání. Primární výjimky jsou ukazatel zásobníku a `malloc` nebo `alloca` paměti, což je zarovnán 16 bajtů za účelem zlepšení výkonu. Zarovnání výše 16 bajtů musí provádět ručně, ale protože je 16 bajtů běžné velikosti zarovnání XMM operací, tento postup měl fungovat pro většinu kódu. Další informace o rozložení struktury a zarovnání naleznete v tématu [typy a úložiště](../build/types-and-storage.md). Informace o rozložení zásobníku, naleznete v tématu [použití zásobníku](../build/stack-usage.md).

## <a name="unwindability"></a>Funkcionalita unwind

Funkce listu jsou funkce, které Neměňte žádné registry není typu volatile. Funkce mimo úroveň listu může změnit stálé RSP, například volání funkce nebo přiděluje další zásobníku pro místní proměnné. Aby bylo možné obnovit bez registry, když je výjimka ošetřena, mimo úroveň listu funkce musí být komentována atributem statická data, která popisuje, jak správně unwind funkci na libovolného instrukce. Tato data se ukládají jako *pdata*, nebo postup dat, které zase odkazuje na *xdata*, zpracování dat výjimek. Xdata odvíjení informacemi a může odkazovat na další pdata nebo funkce obslužné rutiny výjimky. Prology a epilogu funkce jsou vysoce omezenou tak, aby mohly být správně podle xdata. Ukazatel zásobníku musí být zarovnány na 16 bajtů v libovolné oblasti kódu, který není součástí epilogu nebo prologu, s výjimkou v rámci funkcí listu. Funkce listu můžete zachytila jednoduše tak, že budete jen simulovat vrácení, takže pdata a xdata nejsou povinné. Podrobnosti o struktuře správné funkce Prology a epilogu funkce naleznete v tématu [sekvence prologu a epilogu](../build/prolog-and-epilog.md). Další informace o zpracování výjimek a zpracování výjimek a uvolnění pdata a xdata najdete v tématu [Exception Handling (x64)](../build/exception-handling-x64.md).

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](../build/x64-software-conventions.md)