---
title: set_terminate (CRT)
ms.date: 11/04/2016
api_name:
- set_terminate
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
ms.openlocfilehash: 860789a3f2fda5ef13cadffa2a00dba4fbd2090a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948348"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Nainstaluje vlastní rutinu ukončení, která se má volat po **ukončení**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction*<br/>
Ukazatel na funkci ukončení, kterou píšete.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí funkci registrovanou funkcí **set_terminate** , aby bylo možné předchozí funkci obnovit později. Pokud není nastavená žádná předchozí funkce, může se návratová hodnota použít k obnovení výchozího chování; Tato hodnota může být **null**.

## <a name="remarks"></a>Poznámky

Funkce **set_terminate** nainstaluje *termFunction* jako funkci volanou funkcí **ukončit**. **set_terminate** se používá s C++ zpracováním výjimek a může být volána v jakémkoli bodě v programu před tím, než je vyvolána výjimka. **ukončení** volání ve výchozím nastavení [přerušeno](abort.md) . Toto výchozí nastavení můžete změnit vytvořením vlastní ukončovací funkce a voláním **set_terminate** s názvem vaší funkce jako argumentem. **ukončení** volá poslední funkci zadanou jako argument pro **set_terminate**. Po provedení požadovaných úloh vyčištění by *termFunction* mělo ukončit program. Pokud nedojde k ukončení (Pokud se vrátí volajícímu), je volána metoda [Abort](abort.md) .

V prostředí s více vlákny se funkce ukončit uchovávají samostatně pro každé vlákno. Každé nové vlákno musí nainstalovat svou vlastní funkci ukončení. Proto každé vlákno má za následek vlastní zpracování ukončení.

Typ **terminate_function** je definován ve eh. H jako ukazatel na funkci ukončení definované uživatelem, *termFunction* , která vrací **void**. Vlastní *termFunction* funkce nesmí mít žádné argumenty a nemělo by se vracet volajícímu. Pokud k tomu dojde, je volána metoda [Abort](abort.md) . Výjimka nesmí být vyvolána v rámci *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Funkce **set_terminate** funguje pouze mimo ladicí program.

Existuje jedna obslužná rutina **set_terminate** pro všechny dynamicky propojené knihovny DLL nebo exe; i v případě, že zavoláte **set_terminate** , může být obslužná rutina nahrazena jinou nebo může nahradit obslužnou rutinu jinou knihovnou DLL nebo exe.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [ukončení](terminate-crt.md).

## <a name="see-also"></a>Viz také:

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[ruší](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
