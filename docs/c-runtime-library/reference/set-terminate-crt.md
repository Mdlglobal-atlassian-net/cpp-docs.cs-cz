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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 29b760d8831411142aad052fdef510efb0486747
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914522"
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

Vrátí ukazatel na předchozí funkci registrovanou **set_terminate** , aby bylo možné předchozí funkci obnovit později. Pokud není nastavená žádná předchozí funkce, může se návratová hodnota použít k obnovení výchozího chování; Tato hodnota může být **null**.

## <a name="remarks"></a>Poznámky

Funkce **set_terminate** nainstaluje *termFunction* jako funkci volanou funkcí **ukončit**. **set_terminate** se používá při zpracování výjimek jazyka C++ a může být volána v jakémkoli bodě programu před vyvoláním výjimky. **ukončení** volání ve výchozím nastavení [přerušeno](abort.md) . Toto výchozí nastavení můžete změnit vytvořením vlastní ukončovací funkce a voláním **set_terminate** s názvem vaší funkce jako argumentem. **ukončení** volá poslední funkci zadanou jako argument pro **set_terminate**. Po provedení požadovaných úloh vyčištění by *termFunction* mělo ukončit program. Pokud nedojde k ukončení (Pokud se vrátí volajícímu), je volána metoda [Abort](abort.md) .

V prostředí s více vlákny se funkce ukončit uchovávají samostatně pro každé vlákno. Každé nové vlákno musí nainstalovat svou vlastní funkci ukončení. Proto každé vlákno má za následek vlastní zpracování ukončení.

Typ **terminate_function** je definován v eh. H jako ukazatel na funkci ukončení definované uživatelem, *termFunction* , která vrací **void**. Vlastní *termFunction* funkce nesmí mít žádné argumenty a nemělo by se vracet volajícímu. Pokud k tomu dojde, je volána metoda [Abort](abort.md) . Výjimka nesmí být vyvolána v rámci *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Funkce **set_terminate** funguje pouze mimo ladicí program.

Existuje jedna obslužná rutina **set_terminate** pro všechny dynamicky propojené knihovny DLL nebo exe; i v případě, že zavoláte **set_terminate** obslužná rutina může být nahrazena jinou nebo může nahradit obslužnou rutinu jinou knihovnou DLL nebo exe.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_terminate**|\<Eh. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [ukončení](terminate-crt.md).

## <a name="see-also"></a>Viz také

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[přerušit](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[ruší](terminate-crt.md)<br/>
[neočekávané](unexpected-crt.md)<br/>
