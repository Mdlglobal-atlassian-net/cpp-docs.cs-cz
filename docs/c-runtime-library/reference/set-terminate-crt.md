---
title: set_terminate (CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 08ea5bb8c446fadac6a7bcf7ca172c5d14546776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332107"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Nainstaluje vlastní rutinu ukončení, která má být volána **ukončením**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction*<br/>
Ukazatel na funkci ukončení, kterou píšete.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí funkci registrovanou **set_terminate,** aby bylo možné předchozí funkci později obnovit. Pokud nebyla nastavena žádná předchozí funkce, vrácená hodnota může být použita k obnovení výchozího chování; tato hodnota může být **NULL**.

## <a name="remarks"></a>Poznámky

Funkce **set_terminate** nainstaluje *funkci termFunction* jako funkci volanou **funkcí terminate**. **set_terminate** se používá s zpracováním výjimek jazyka C++ a může být volána v libovolném bodě programu před vyvolání výjimky. **ve** výchozím nastavení [přerušit přerušení](abort.md) volání. Toto výchozí nastavení můžete změnit zápisem vlastní funkce ukončení a voláním **set_terminate** s názvem funkce jako argumentem. **ukončit** volání poslední funkce uvedené jako argument **k set_terminate**. Po provedení všech požadovaných úloh *vyčištění, termFunction* by měl ukončit program. Pokud není ukončení (pokud se vrátí volajícímu), [abort](abort.md) je volána.

V prostředí s více vlákny jsou funkce ukončení udržovány samostatně pro každé vlákno. Každé nové vlákno musí nainstalovat vlastní funkci ukončení. To znamená, že každé vlákno má na starosti vlastní zpracování ukončení.

Typ **terminate_function** je definován v EH. H jako ukazatel na uživatelem definovanou koncovou funkci *termFunction,* která vrací **funkci void**. Vaše vlastní funkce *termFunction* může trvat žádné argumenty a nemělby se vrátit k jeho volajícímu. Pokud ano, [abort](abort.md) je volána. Výjimka nesmí být vyvolána z v rámci *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Funkce **set_terminate** funguje pouze mimo ladicí program.

Existuje jedna obslužná rutina **set_terminate** pro všechny dynamicky propojené knihovny DLL nebo EXE; i v případě, že zavoláte **set_terminate** může být vaše obslužná rutina nahrazena jinou, nebo nahrazujete obslužnou rutinu nastavenou jinou dll nebo EXE.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [terminate](terminate-crt.md).

## <a name="see-also"></a>Viz také

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[Přerušení](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Ukončit](terminate-crt.md)<br/>
[Neočekávané](unexpected-crt.md)<br/>
