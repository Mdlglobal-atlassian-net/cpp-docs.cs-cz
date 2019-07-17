---
title: _set_se_translator
ms.date: 02/21/2018
apiname:
- _set_se_translator
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
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 23eb4e9016666567771832cefed686cb9197b02f
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299712"
---
# <a name="setsetranslator"></a>_set_se_translator

Nastavte funkci zpětného volání pro vlákno pro převod výjimek Win32 (strukturované výjimky jazyka C) C++ na typové výjimky.

## <a name="syntax"></a>Syntaxe

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parametry

*seTransFunction*<br/>
Ukazatel na funkci překladače strukturované výjimky jazyka C, kterou zapisujete.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí funkci překladače zaregistrovanou funkcí **_set_se_translator**, aby bylo možné předchozí funkci obnovit později. Pokud není nastavená žádná předchozí funkce, můžete k obnovení výchozího chování použít návratovou hodnotu. Tato hodnota může být **nullptr**.

## <a name="remarks"></a>Poznámky

Funkce **_set_se_translator** poskytuje způsob, jak zpracovat výjimky Win32 (strukturované výjimky jazyka C) jako C++ typové výjimky. Chcete-li, aby každá výjimka jazyka c mohla C++ být zpracována obslužnou rutinou **catch** , nejprve definujte obálkovou třídu výjimky jazyka c, která může být použita nebo odvozena z, k atributu určitého typu třídy na výjimku jazyka C. Chcete-li použít tuto třídu, nainstalujte vlastní funkci překladače výjimky jazyka C, která je volána interním mechanismem zpracování výjimky pokaždé, když je vyvolána výjimka jazyka C. V rámci funkce překladatele můžete vyvolat jakoukoli typovou výjimku, kterou lze zachytit pomocí odpovídající C++ obslužné rutiny **catch** .

[/EHa](../../build/reference/eh-exception-handling-model.md) je nutné použít při použití **_set_se_translator**.

Chcete-li zadat vlastní funkci překladu, zavolejte **_set_se_translator** pomocí názvu funkce překladu jako argumentu. Funkce překladatele, kterou napíšete, je volána jednou pro každé vyvolání funkce v zásobníku, která obsahuje bloky **Try** . Neexistuje žádná výchozí funkce překladače.

Funkce překladače by neměla dělat více než vyvolat C++ typovou výjimku. V případě, že kromě toho dojde k vyvolání (například při zápisu do souboru protokolu), se program nemusí chovat podle očekávání, protože počet volání funkce překladače je závislý na platformě.

V prostředí s více vlákny jsou funkce překladatele uchovávány samostatně pro každé vlákno. Každé nové vlákno musí nainstalovat svou vlastní funkci překladatele. Proto každé vlákno má za následek vlastní zpracování překladu. **_set_se_translator** je specifický pro jedno vlákno; Jiná knihovna DLL může nainstalovat jinou funkci překladu.

Funkce *seTransFunction* , kterou napíšete, musí být nativní kompilovaná funkce (není zkompilována s/CLR). Musí přebírat unsigned integer a jako argumenty **_EXCEPTION_POINTERS** strukturu Win32. Argumenty jsou návratové hodnoty volání funkce Win32 API **GetExceptionCode** a **GetExceptionInformation** , v uvedeném pořadí.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Pro **_set_se_translator**existují důsledky Při dynamickém propojení s CRT; Jiná knihovna DLL v procesu může volat **_set_se_translator** a nahradit svou obslužnou rutinu vlastními.

Při použití **_set_se_translator** ze spravovaného kódu (kód kompilovaný s/CLR) nebo smíšeným nativním a spravovaným kódem je třeba si uvědomit, že Překladatel ovlivňuje pouze výjimky vygenerované pouze v nativním kódu. Jakékoli spravované výjimky vygenerované ve spravovaném kódu (například při `System::Exception`vyvolávání) nejsou směrovány pomocí funkce Translator. Výjimky vyvolané ve spravovaném kódu pomocí funkce Win32 **RaiseException –** nebo způsobené výjimkou systému, jako je dělení nulou, jsou směrovány prostřednictvím překladatele.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tato ukázka zabalí volání pro nastavení překladatele strukturované výjimky a obnoví starou třídu RAII, `Scoped_SE_Translator`. Tato třída umožňuje zavést překladatele specifický pro obor jako jednu deklaraci. Destruktor třídy obnoví původní překladatel, když ovládací prvek opustí rozsah.

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Příklad

Přestože funkce, které poskytuje **_set_se_translator** , nejsou ve spravovaném kódu k dispozici, je možné použít toto mapování v nativním kódu, a to i v případě, že je tento nativní kód v kompilaci pod přepínačem **/CLR** , pokud je nativní kód označené pomocí `#pragma unmanaged`. Pokud dojde k vyvolání strukturované výjimky ve spravovaném kódu, který má být namapován, je nutné označit `#pragma unmanaged`kód, který generuje a zpracuje výjimku. Následující kód ukazuje možné použití. Další informace naleznete v tématu [direktivy pragma a klíčové slovo __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Viz také:

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[ruší](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
