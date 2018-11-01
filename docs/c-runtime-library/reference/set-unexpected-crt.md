---
title: set_unexpected (CRT)
ms.date: 11/04/2016
apiname:
- set_unexpected
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
apitype: DLLExport
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 6c38421e447ca7b3f263148f51f0ade5c59e2804
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484224"
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

Nainstaluje vlastní funkci ukončení má být volána **neočekávané**.

## <a name="syntax"></a>Syntaxe

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parametry

*unexpFunction*<br/>
Ukazatel na funkci, která zapíšete do nahradit **neočekávané** funkce.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na funkci předchozí ukončení registrovaných **_set_unexpected** tak, aby předchozí funkci lze později obnovit. Pokud byla nastavena žádná předchozí funkce, vrácená hodnota slouží k obnovení výchozího chování; Tato hodnota může být **NULL**.

## <a name="remarks"></a>Poznámky

**Set_unexpected** funkce nainstaluje *unexpFunction* jako funkci volanou třídou **neočekávané**. **neočekávané** se nepoužívá v aktuální implementace zpracování výjimek jazyka C++. **Unexpected_function** typ je definován v EH. H jako ukazatel na uživatelské neočekávané funkce *unexpFunction* , která vrací **void**. Vaše vlastní *unexpFunction* funkce by neměly vracet volajícímu.

```cpp
typedef void ( *unexpected_function )( );
```

Ve výchozím nastavení **neočekávané** volání **ukončit**. Můžete změnit toto výchozí chování psaní vlastních ukončení funkce a volání **set_unexpected** s názvem funkce jako svůj argument. **neočekávané** volá poslední funkci předána jako argument pro **set_unexpected**.

Na rozdíl od vlastních ukončení funkce nainstalované voláním **set_terminate**, může být vyvolána výjimka v rámci *unexpFunction*.

V prostředí s více vlákny jsou neočekávané funkce udržovány odděleně pro každé vlákno. Každé nové vlákno je potřeba nainstalovat neočekávané funkce. Díky tomu se každé vlákno má na starosti vlastní neočekávané zpracování.

V aktuální implementaci zpracování výjimek jazyka C++ společnosti Microsoft **neočekávané** volání **ukončit** ve výchozím nastavení a nikdy volán knihovny run-time zpracování výjimek. Neexistuje žádná konkrétní výhoda volání **neočekávané** spíše než **ukončit**.

Existuje jeden **set_unexpected** obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo exe; i v případě, že zavoláte **set_unexpected** vaše obslužná rutina může být nahrazena jinou nebo nahrazujete obslužnou rutinu nastavením jiného souboru DLL nebo EXE.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[ukončit](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
