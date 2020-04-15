---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 5a0011d11e4a59c9ca3a5e18f44d4cf831b21582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366649"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

Specifikátor omezení lze použít pro deklarace funkce i výrazu lambda. Vynucuje omezení kódu ve funkci a chování funkce v aplikacích používajících modul runtime C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Informace o **klíčovém** slově restrict, které je součástí atributů **třídy** úložiště __declspec, naleznete v [tématu omezení](../cpp/restrict.md).

Klauzule **restrict** má následující formy:

|Klauzule|Popis|
|------------|-----------------|
|`restrict(cpu)`|Funkce může využívat celý jazyk C++. Funkci mohou volat pouze jiné funkce deklarované pomocí funkcí restrict(cpu).|
|`restrict(amp)`|Funkce může používat pouze tu podmnožinu jazyka C++, kterou může knihovna C++ AMP urychlit.|
|Sekvence specifikátorů `restrict(cpu)` a `restrict(amp)`.|Funkce musí dodržovat omezení specifikátoru `restrict(cpu)` i `restrict(amp)`. Funkci lze zavolat funkcemi deklarovanými pomocí specifikátorů `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` nebo `restrict(amp, cpu)`.<br /><br /> Tvar `restrict(A) restrict(B)` lze zapsat jako `restrict(A,B)`.|

## <a name="remarks"></a>Poznámky

Klíčové slovo **restrict** je kontextové klíčové slovo. Specifikátory omezení `cpu` a `amp` nejsou vyhrazenými slovy. Seznam specifikátorů nelze rozšířit. Funkce, která nemá **klauzuli restrict,** je stejná `restrict(cpu)` jako funkce, která má klauzuli.

Funkce obsahující klauzuli `restrict(amp)` má následující omezení:

- Funkce může volat pouze funkce obsahující klauzuli `restrict(amp)`.

- Funkci musí být možné vložit.

- Funkce může deklarovat pouze **int**, **nepodepsané int**, **float**a **dvojité** proměnné a třídy a struktury, které obsahují pouze tyto typy. **bool** je také povolena, ale musí být zarovnána 4 bajty, pokud jej používáte ve složeném typu.

- Funkce lambda nedokážou zachytit ukazatele a hodnoty dle reference.

- Reference a ukazatele jedné dereference jsou podporovány pouze jako místní proměnné, argumenty funkce a návratové typy.

- Následující položky nejsou povoleny:

  - Rekurze.

  - Proměnné deklarované pomocí klíčového slova [volatile.](../cpp/volatile-cpp.md)

  - Virtuální funkce.

  - Ukazatele na funkce.

  - Ukazatele na členské funkce.

  - Ukazatele ve strukturách.

  - Ukazatele na ukazatele.

  - **goto** prohlášení.

  - Příkazy s popisky.

  - **try**, **catch**nebo **throw** statements .

  - Globální proměnné.

  - Statické proměnné. Místo toho použijte [klíčové slovo tile_static.](../cpp/tile-static-keyword.md)

  - **dynamic_cast** odlitky.

  - Operátor **typeid.**

  - Deklarace asm.

  - Argumenty vararg.

Diskuse o omezení funkcí naleznete v tématu [omezení (amp) Omezení](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `restrict(amp)`používat klauzuli.

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>Viz také

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
