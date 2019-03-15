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
ms.openlocfilehash: 18ee500d7b884d1934c29dc91d9bcb03d507680d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808375"
---
# <a name="setsetranslator"></a>_set_se_translator

Nastavte výjimky typu funkce zpětného volání na vlákno pro převod výjimky Win32 (strukturované výjimky jazyka C) na C++.

## <a name="syntax"></a>Syntaxe

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parametry

*seTransFunction*<br/>
Ukazatel na C strukturované výjimky funkce translator, který píšete.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na funkci předchozí translator registrovaných **_set_se_translator**, takže lze později obnovit předchozí funkce. Pokud byla nastavena žádná předchozí funkce, vrácená hodnota je možné obnovit výchozí chování; Tato hodnota může být **nullptr**.

## <a name="remarks"></a>Poznámky

**_Set_se_translator** poskytuje způsob, jak zpracovat výjimky Win32 (strukturované výjimky jazyka C) jako C++ – funkce typu výjimky. Chcete-li povolit jednotlivé výjimky jazyka C++ zpracovávat **catch** obslužnou rutinu, nejprve definují C obálkovou třídu výjimek, který můžete použít nebo odvodit, kterému budou připsány určitý typ třídy na výjimku jazyka C. Pokud chcete použít tuto třídu, nainstalujte vlastní funkci C výjimka translator, která je volána metodou interní mechanismus zpracování výjimek pokaždé, když je vyvolána výjimka jazyka C. V rámci funkce translator, lze vyvolat jakoukoli typovou výjimku, které lze zachytit odpovídající C++ **catch** obslužné rutiny.

Je nutné použít [/EHa](../../build/reference/eh-exception-handling-model.md) při použití **_set_se_translator**.

Chcete-li zadat vlastní funkci překladu, zavolejte **_set_se_translator** pomocí názvu funkce překladu jako její argument. Funkce translator, který píšete se volá jednou pro každé vyvolání funkce v zásobníku, který má **zkuste** bloky. Neexistuje žádný výchozí převaděč funkce.

Funkce translator by měl provádět žádné další než výjimku jazyka C++ zadané výjimky. Pokud už existoval nic kromě vyvolání (jako je například zápis do souboru protokolu, třeba) aplikace nemusí chovat dle očekávání, protože počet, kolikrát vyvolání této funkce translator závisí na platformě.

V prostředí s více vlákny jsou funkce překladatele udržovány odděleně pro každé vlákno. Je potřeba nainstalovat vlastní funkci translator každém novém vláknu. Díky tomu se každé vlákno má na starosti vlastní zpracování překladu. **_set_se_translator** je specifický pro jedno vlákno; jiné knihovně DLL můžete nainstalovat funkce různých překladu.

*SeTransFunction* vytvořená funkce musí být funkce nativně kompilovaného (ne zkompilovanou pomocí/CLR). Celé číslo bez znaménka a ukazatel je nutné provést při Win32 **_exception_pointers –** struktury jako argumenty. Argumenty jsou vrácené hodnoty volání rozhraní API systému Win32 **GetExceptionCode** a **GetExceptionInformation** funguje, v uvedeném pořadí.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Pro **_set_se_translator**, když dynamického propojení ke CRT jsou důsledky; jiné knihovny DLL v procesu může volat **_set_se_translator** a nahradit vlastní obslužnou rutinu.

Při použití **_set_se_translator** ze spravovaného kódu (kód zkompilovaný s parametrem/CLR) nebo smíšeného nativního a spravovaného kódu, mějte na paměti, které ovlivňuje překladač výjimky generované v pouze nativního kódu. Některé spravované výjimky generované ve spravovaném kódu (třeba při vyvolání `System::Exception`) nejsou směrovány prostřednictvím funkce translator. Výjimky vyvolané ve spravovaném kódu použitím funkce Win32 **RaiseException** nebo způsobeno výjimkou systému, jako jsou dělení nulovou výjimkou jsou směrovány překladač.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

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
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception( unsigned int n ) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
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

void trans_func(unsigned int u, EXCEPTION_POINTERS*)
{
    throw SE_Exception(u);
}

int main()
{
    auto original = _set_se_translator(trans_func);
    try
    {
        SEFunc();
    }
    catch(SE_Exception& e)
    {
        printf("Caught a __try exception, error %8.8x.\n", e.getSeNumber());
    }
    _set_se_translator(original);
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Příklad

I když funkce poskytované **_set_se_translator** není k dispozici ve spravovaném kódu, je možné použít toto mapování v nativním kódu i v případě, že nativního kódu je v kompilaci v části **/CLR** Přepnout, tak dlouho, dokud nativního kódu je označen pomocí `#pragma unmanaged`. Pokud se strukturovaná výjimka je vyvolávána ve spravovaném kódu, který se má namapovat, musí být označen kód, který generuje a zpracovává výjimku `#pragma unmanaged`. Následující kód ukazuje možné použít. Další informace najdete v tématu [direktivy Pragma a klíčové slovo __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>
#include <exception>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception {
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw SE_Exception(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(SE_Exception& e)
    {
        printf("Caught SE_Exception, error %8.8x\n", e.getSeNumber());
    }
    catch(...)
    {
        printf("Caught unexpected SEH exception.\n");
    }
}
#pragma managed

int main() {
    auto original = _set_se_translator(my_trans_func);
    DoTest();
    _set_se_translator(original);
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Viz také:

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[ukončit](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
