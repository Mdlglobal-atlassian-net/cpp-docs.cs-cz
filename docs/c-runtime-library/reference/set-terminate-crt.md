---
title: set_terminate (CRT)
ms.date: 11/04/2016
apiname:
- set_terminate
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 7be81dec7fba80a273d635cbd30b96b09928bc66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493909"
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

Nainstaluje si vlastní rutinu ukončení, které jsou volány **ukončit**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction*<br/>
Ukazatel na funkci ukončení, který píšete.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na funkci předchozí registrovaných **set_terminate** tak, aby předchozí funkci lze později obnovit. Pokud byla nastavena žádná předchozí funkce, vrácená hodnota slouží k obnovení výchozího chování; Tato hodnota může být **NULL**.

## <a name="remarks"></a>Poznámky

**Set_terminate** funkce nainstaluje *termFunction* jako funkci volanou třídou **ukončit**. **set_terminate** se používá s zpracování výjimek jazyka C++ a může být volána v libovolném bodě ve svém programu, než je vyvolána výjimka. **Ukončit** volání [přerušit](abort.md) ve výchozím nastavení. Toto výchozí nastavení můžete změnit tak, že zápis ukončení funkce a volání **set_terminate** s názvem funkce jako svůj argument. **Ukončit** volá poslední funkci předána jako argument pro **set_terminate**. Po provedení některé požadované úlohy čištění, *termFunction* by měla ukončit program. Pokud neexistuje (Pokud se vrátí výsledek volajícímu), [přerušit](abort.md) je volána.

V prostředí s více vlákny ukončení funkce jsou udržovány odděleně pro každé vlákno. Každé nové vlákno je potřeba nainstalovat vlastní funkci terminate. Díky tomu se každé vlákno má na starosti vlastní zpracování ukončení.

**Terminate_function –** typ je definován v EH. H jako ukazatel na ukončení uživatelem definované funkce, *termFunction* , která vrací **void**. Vaše vlastní funkce *termFunction* můžete nepřebírají žádné argumenty a by neměly vracet volajícímu. Pokud ano, [přerušit](abort.md) je volána. Nemusí být vyvolána výjimka v rámci *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate** funkce funguje pouze mimo ladicí program.

Existuje jeden **set_terminate** obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo exe; i v případě, že zavoláte **set_terminate** vaše obslužná rutina může být nahrazena jinou, nebo může být nahrazení nastavena jiná obslužná rutina Knihovna DLL nebo EXE.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [ukončit](terminate-crt.md).

## <a name="see-also"></a>Viz také:

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[ukončit](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
