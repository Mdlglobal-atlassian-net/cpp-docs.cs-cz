---
title: set_terminate – (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02c38d8c832c4b84725dc15c280c8b3f3fd27841
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

Nainstaluje vlastní rutiny ukončení má být volána **ukončit**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction*<br/>
Ukazatel na funkci ukončit, která můžete zapsat.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na funkci předchozí registrovaných **set_terminate –** , aby předchozí funkce můžete později obnovit. Pokud byla nastavena žádná předchozí funkce, návratovou hodnotu může použít k obnovení výchozího chování; Tato hodnota může mít hodnotu NULL.

## <a name="remarks"></a>Poznámky

**Set_terminate –** funkce nainstaluje *termFunction* jako funkce volá **ukončit**. **set_terminate –** se používá s zpracovávání výjimek v jazyce C++ a může být volána v libovolném bodě v programu, než je vyvolána výjimka. **Ukončit** volání [abort](abort.md) ve výchozím nastavení. Toto výchozí nastavení můžete změnit tak, že zápis ukončení funkce a volání **set_terminate –** s názvem funkce jako její argument. **Ukončit** volá funkci naposledy zadaný jako argument pro **set_terminate –**. Po provedení všechny potřeby úlohy čištění, *termFunction* programu musí ukončit. Pokud neexistuje (Pokud se vrátí do jeho volajícího), [abort](abort.md) je volána.

V prostředí s více vlákny ukončit funkce jsou udržovány odděleně pro každé vlákno. Každé vlákno je potřeba nainstalovat svou vlastní funkci ukončit. Proto každé vlákno má na starosti vlastní zpracování ukončení.

**Terminate_function –** typ je definována v EH. H jako ukazatel na funkci ukončení definovaný uživatelem, *termFunction* , který vrací **void**. Vaše vlastní funkce *termFunction* můžete nepřebírají žádné argumenty a by neměla vrátit do jeho volajícího. Pokud ano, [abort](abort.md) je volána. Nemusí být vyvolána výjimka uvnitř *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate –** funkce funguje pouze mimo ladicí program.

Na jeden **set_terminate –** obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo exe soubory; i v případě, že zavoláte **set_terminate –** vaší obslužné rutiny, může být nahrazen jiným, nebo může být nahrazení nastavit jiná obslužná rutina Knihovny DLL nebo EXE.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [ukončit](terminate-crt.md).

## <a name="see-also"></a>Viz také

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Ukončení](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
