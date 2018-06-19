---
title: set_unexpected – (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7af5cce0b17747beb8c136f75489025d741f864a
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451872"
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

Nainstaluje ukončení funkce má být volána **neočekávané**.

## <a name="syntax"></a>Syntaxe

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parametry

*unexpFunction*<br/>
Ukazatel na funkci, která můžete psát nahradit **neočekávané** funkce.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na funkci předchozí ukončení registrovaných **_set_unexpected** , aby předchozí funkce můžete později obnovit. Pokud byla nastavena žádná předchozí funkce, návratovou hodnotu může použít k obnovení výchozího chování; Tato hodnota může být **NULL**.

## <a name="remarks"></a>Poznámky

**Set_unexpected –** funkce nainstaluje *unexpFunction* jako funkce volá **neočekávané**. **neočekávané** není používán aktuální implementace zpracování výjimek C++. **Unexpected_function – definice** typ je definována v EH. H jako ukazatel na uživatelem definované neočekávaná funkce *unexpFunction* , který vrací **void**. Vaše vlastní *unexpFunction* funkce by neměla vrátit do jeho volajícího.

```cpp
typedef void ( *unexpected_function )( );
```

Ve výchozím nastavení **neočekávané** volání **ukončit**. Toto výchozí chování můžete změnit tak, že zápis ukončení funkce a volání **set_unexpected –** s názvem funkce jako její argument. **neočekávané** volá funkci naposledy zadaný jako argument pro **set_unexpected –**.

Na rozdíl od nainstalované ve volání funkce vlastní ukončení **set_terminate –**, můžete v rámci vyvolána výjimka *unexpFunction*.

V prostředí s více vlákny neočekávané funkce jsou pro každé vlákno udržovány odděleně. Každé vlákno je potřeba nainstalovat vlastní neočekávaná funkce. Proto každé vlákno má na starosti vlastní neočekávané zpracování.

Zpracovávání výjimek v jazyce C++, aktuální implementace Microsoft **neočekávané** volání **ukončit** ve výchozím nastavení a nikdy volá knihovna RTL – zpracování výjimek. Neexistuje žádné konkrétní výhody volání **neočekávané** místo **ukončit**.

Na jeden **set_unexpected –** obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo exe soubory; i v případě, že zavoláte **set_unexpected –** vaší obslužné rutiny, může být nahrazen jiným nebo který chcete nahradit obslužnou rutinu, která nastavuje jiné knihovny DLL nebo EXE.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[Ukončení](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
