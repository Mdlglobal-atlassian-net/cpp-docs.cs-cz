---
title: set_unexpected (CRT)
ms.date: 11/04/2016
api_name:
- set_unexpected
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 77c8f0ae8c64423a656a2ebbe1fe3ef6dbe1b794
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948307"
---
# <a name="set_unexpected-crt"></a>set_unexpected (CRT)

Nainstaluje vaši vlastní funkci ukončení, která se bude volat **neočekávaným**.

## <a name="syntax"></a>Syntaxe

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parametry

*unexpFunction*<br/>
Ukazatel na funkci, kterou napíšete, chcete-li nahradit **neočekávanou** funkci.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí funkci ukončení registrovanou funkcí **_set_unexpected** , aby bylo možné předchozí funkci obnovit později. Pokud není nastavená žádná předchozí funkce, může se návratová hodnota použít k obnovení výchozího chování; Tato hodnota může být **null**.

## <a name="remarks"></a>Poznámky

Funkce **set_unexpected** nainstaluje *unexpFunction* jako funkci volanou **neočekávanou**. **neočekávaná** implementace se nepoužívá v C++ aktuální implementaci zpracování výjimek. Typ **unexpected_function** je definován ve eh. H jako ukazatel na uživatelem definovanou neočekávanou funkci *unexpFunction* , která vrací **void**. Vaše vlastní funkce *unexpFunction* by se neměla vracet volajícímu.

```cpp
typedef void ( *unexpected_function )( );
```

Ve výchozím nastavení **končí** **neočekávaná** volání. Toto výchozí chování můžete změnit vytvořením vlastní funkce ukončení a voláním **set_unexpected** s názvem vaší funkce jako argumentem. **neočekávaná** volání poslední funkce zadané jako argument pro **set_unexpected**.

Na rozdíl od funkce vlastní ukončení nainstalované voláním **set_terminate**může být výjimka vyvolána v rámci *unexpFunction*.

V prostředí s více vlákny se neočekávané funkce uchovávají samostatně pro každé vlákno. Každé nové vlákno musí nainstalovat svou vlastní neočekávanou funkci. Proto každé vlákno má za následek neočekávané zpracování.

V současné implementaci zpracování výjimek od C++ společnosti Microsoft je **neočekávané** volání ve výchozím nastavení **ukončeno** a není nikdy voláno knihovnou run-time zpracovávající výjimky. Není k dispozici žádná zvláštní výhoda pro volání **neočekávaného** neúplného **ukončení**.

Existuje jedna obslužná rutina **set_unexpected** pro všechny dynamicky propojené knihovny DLL nebo exe; i v případě, že zavoláte **set_unexpected** , může být obslužná rutina nahrazena jinou nebo, kterou nahrazujete obslužnou rutinu nastavenou jinou knihovnou DLL nebo exe.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[ruší](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
