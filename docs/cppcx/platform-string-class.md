---
title: Platform::String – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: 0b8a29efc5b18432eabfeddc75af12737538281c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330203"
---
# <a name="platformstring-class"></a>Platform::String – třída

Představuje kolekci sekvenční znaků Unicode, který se používá k reprezentaci textu. Další informace a příklady najdete v tématu [řetězce](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterátory

Dvě funkce iterátoru, které nejsou členy třídy řetězec, je možné s `std::for_each` funkce šablony vytvořit výčet znaky v objektu typu String.

|Člen|Popis|
|------------|-----------------|
|`const char16* begin(String^ s)`|Vrací ukazatel na začátek zadaného objektu String.|
|`const char16* end(String^ s)`|Vrací ukazatel ukazující za zadaný objekt řetězce.|

### <a name="members"></a>Členové

Třída String dědí z objektu a rozhraní IDisposable, IEquatable a IPrintable.

Třída String má také následující typy členů.

**Konstruktory**

|Člen|Popis|
|------------|-----------------|
|[String::String](#ctor)|Inicializuje novou instanci třídy řetězec.|

**Metody**

Třída String dědí metody Equals() Finalize(), GetHashCode(), GetType(), MemberwiseClose() a ToString() z [Platform::Object – třída](../cppcx/platform-object-class.md). Řetězec má také následující metody.

|Metoda|Popis|
|------------|-----------------|
|[String::begin](#begin)|Vrací ukazatel na začátek aktuálního řetězce.|
|[String::CompareOrdinal](#compareordinal)|Porovná dva `String` objekty vyhodnocením číselné hodnoty odpovídající znaky v dva řetězcové hodnoty reprezentována objekty.|
|[String::concat](#concat)|Zřetězí hodnoty ze dvou řetězcových objektů.|
|[String::Data](#data)|Vrací ukazatel na začátek aktuálního řetězce.|
|[String::dispose](#dispose)|Uvolní nebo uvolní prostředky.|
|[String::end](#end)|Vrací ukazatel ukazující za hranice aktuální řetězce.|
|[String::Equals](#equals)|Určuje, zda zadaný objekt rovná aktuálnímu objektu.|
|[String::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|
|[String::IsEmpty](#isempty)|Určuje, zda je aktuální objekt řetězec prázdný.|
|[String::IsFastPass](#isfastpass)|Určuje, zda se účastní na aktuální objekt řetězce *fast pass* operace. V rychlé splnění operace, počítání odkazů je pozastaveno.|
|[String::length](#length)|Načte délku na aktuální objekt řetězce.|
|[String::ToString](#tostring)|Vrátí objekt String, jehož hodnota je stejná jako aktuální řetězec.|

**Operátory**

Třída řetězec má následující operátory.

|Člen|Popis|
|------------|-----------------|
|[String::Operator == – operátor](#operator-equality)|Určuje, zda dva objekty zadaného řetězce mají stejnou hodnotu.|
|[Operator + – operátor](#operator-plus)|Zřetězí dva objekty řetězce do nového objektu řetězce.|
|[String::Operator > – operátor](#operator-greater-than)|Určuje, zda je hodnota jednoho objektu řetězec větší než hodnota druhý objekt řetězce.|
|[String::Operator > = – operátor](#operator-greater-than-or-equals)|Určuje, zda je hodnota jednoho objektu řetězec větší nebo rovna hodnotě druhý objekt řetězce.|
|[String::Operator! = – operátor](#operator-inequality)|Určuje, zda dva objekty zadaného řetězce mají různé hodnoty.|
|[String::Operator < – operátor](#operator-less-than)|Určuje, zda je hodnota jednoho objektu řetězce menší než hodnota druhý objekt řetězce.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Hlavička** vccorlib.h (zahrnuté ve výchozím nastavení)

## <a name="begin"></a>  String::begin – metoda

Vrací ukazatel na začátek aktuálního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
char16* Begin();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek aktuálního řetězce.

## <a name="compareordinal"></a>  String::CompareOrdinal – metoda

Porovná dva `String` objekty vyhodnocením číselné hodnoty odpovídající znaky v dva řetězcové hodnoty reprezentována objekty.

### <a name="syntax"></a>Syntaxe

```cpp
int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První řetězec objektu.

*str2*<br/>
Druhý objekt řetězce.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které označuje lexikální vztah mezi dvěma komparátory. Následující tabulka obsahuje seznam možných vrácených hodnot.

|Value|Podmínka|
|-----------|---------------|
|-1|`str1` je menší než `str2`.|
|0|`str1` je rovno `str2`.|
|1|`str1` je větší než `str2`.|

## <a name="concat"></a>  String::concat – metoda

Zřetězí hodnoty ze dvou řetězcových objektů.

### <a name="syntax"></a>Syntaxe

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První řetězec objektu, nebo `null`.

*str2*<br/>
Druhý objekt řetězce nebo `null`.

### <a name="return-value"></a>Návratová hodnota

Nový řetězec ^ objekt, jehož hodnota je zřetězením hodnoty z `str1` a `str2`.

Pokud `str1` je `null` a `str2` není, `str1` je vrácena. Pokud `str2` je `null` a `str1` není, `str2` je vrácena. Pokud `str1` a `str2` jsou obě `null`, prázdný řetězec (L"") se vrátí.

## <a name="data"></a>  String::data – metoda

Vrací ukazatel na začátek vyrovnávací paměti dat objektu jako pole stylu C `char16` (`wchar_t`) elementy.

### <a name="syntax"></a>Syntaxe

```
const char16* Data();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátku `const char16` pole znaků Unicode (`char16` je definice typu `wchar_t`).

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete převést z `Platform::String^` k `wchar_t*`. Když `String` objekt dostane mimo rozsah, ukazatel datového již není zaručeno platný. K ukládání dat nad rámec doby života původní `String` objektu, použijte [wcscpy_s –](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) ke kopírování pole do paměti, které jste přidělili sami.

## <a name="dispose"></a>  String::Dispose – metoda

Uvolní nebo uvolní prostředky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override void Dispose();
```

## <a name="end"></a>  String::end – metoda

Vrací ukazatel ukazující za hranice aktuální řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
char16* End();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel ukazující za hranice aktuální řetězce.

### <a name="remarks"></a>Poznámky

End() returns Begin() + Length.

## <a name="equals"></a>  String::Equals – metoda

Určuje, jestli zadaný řetězec má stejnou hodnotu jako aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `str` je rovná aktuálnímu objektu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato metoda je ekvivalentní [String::CompareOrdinal](#compareordinal). V první přetížení se očekává `str` parametr může být převeden na řetězec ^ objektu.

## <a name="gethashcode"></a>  String::GetHashCode – metoda

Vrátí kód hash této instance.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Kód hash této instance

## <a name="isempty"></a>  String::IsEmpty – metoda

Určuje, zda je aktuální objekt řetězec prázdný.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Návratová hodnota

**true** Pokud aktuální `String` objekt **null** nebo prázdný řetězec (L""); v opačném případě **false**.

## <a name="isfastpass"></a>  String::IsFastPass – metoda

Určuje, zda se účastní na aktuální objekt řetězce *fast pass* operace. V rychlé splnění operace, počítání odkazů je pozastaveno.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální `String` minulosti fast; v opačném případě je objekt **false**.

### <a name="remarks"></a>Poznámky

Ve volání funkce, kde objekt referenčně započítaný je parametr a volané funkce přečte pouze tento objekt kompilátor bezpečně pozastavit počítání odkazů a zlepšit výkon volání. Není co užitečné, že váš kód můžete dělat s touto vlastností. Systém zpracovává všechny podrobnosti.

## <a name="length"></a>  String::length – metoda

Získá počet znaků v aktuální `String` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků v aktuální `String` objektu.

### <a name="remarks"></a>Poznámky

Délka řetězce se žádné znaky je nula. Tento řetězec je 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Znak pole vrácené metodou [String::Data](#data) obsahuje jeden další znak, který je ukončující hodnotu NULL nebo '\0'. Tento znak je také dva bajty.

## <a name="operator-plus"></a>  String::Operator + – operátor

Zřetězí dva [řetězec](../cppcx/platform-string-class.md) objektů do nového [řetězec](../cppcx/platform-string-class.md) objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objektu.

*str2*<br/>
Druhá `String` objekt, jehož obsah se připojí k `str1`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *str1* rovná *řetězci str2*; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento operátor vytvoří `String^` objekt, který obsahuje data ze dvou operandů. Používejte ke zvýšení pohodlí Pokud mimořádný výkon není důležité. Několik volání "`+`" ve funkci budou pravděpodobně není patrné, ale pokud manipulaci velké objekty nebo textová data v těsné smyčce použijte standardní mechanismy C++ a typy.

##  <a name="operator-equality"></a> String::Operator == – operátor

Určuje, zda dva objekty zadaného řetězce mají stejnou textovou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt k porovnání.

*str2*<br/>
Druhá `String` objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud obsah `str1` rovnají `str2`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento operátor je ekvivalentní [String::CompareOrdinal](#compareordinal).

##  <a name="operator-greater-than"></a>  String::Operator&gt;

Určuje, zda hodnota jednoho `String` objekt je větší než hodnota sekundy `String` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objektu.

*str2*<br/>
Druhá `String` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hodnota `str1` je větší než hodnota `str2`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento operátor je ekvivalentní explicitně voláním [String::CompareOrdinal](#compareordinal) a získání výsledku větší než nula.

## <a name="operator-greater-than-or-equals"></a> String::Operator&gt;=

Určuje, zda hodnota jednoho `String` objekt je větší než nebo rovna hodnotě sekundy `String` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objektu.

*str2*<br/>
Druhá `String` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hodnota `str1` je větší než nebo rovna hodnotě tohoto `str2`; v opačném případě **false**.

## <a name="operator-inequality"></a> String::Operator! =

Určuje, zda dvě zadané `String` objekty mají různé hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt k porovnání.

*str2*<br/>
Druhá `String` objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `str1` není roven `str2`; v opačném případě **false**.

## <a name="operator-less-than"></a> String::Operator&lt;

Určuje, zda hodnota jednoho `String` je objekt menší než hodnota sekundy `String` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objektu.

*str2*<br/>
Druhá `String` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hodnota *str1* je menší než hodnota *řetězci str2*; v opačném případě **false**.

## <a name="ctor"></a> String::String konstruktor

Inicializuje novou instanci třídy `String` třídy pomocí kopírovaných dat vstupního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parametry

*s*<br/>
Řada široké znaky, které Inicializuje řetězec. char16

*n*<br/>
Číslo, které určuje délku řetězce.

### <a name="remarks"></a>Poznámky

Pokud je nejdůležitější výkon a řídit dobu života zdrojový řetězec, můžete použít [Platform::stringreference –](../cppcx/platform-stringreference-class.md) namísto řetězce.
### <a name="example"></a>Příklad

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a> String::ToString

Vrátí `String` objekt, jehož hodnota je stejná jako aktuální řetězec.

### <a name="syntax"></a>Syntaxe

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Návratová hodnota

A `String` objekt, jehož hodnota je stejná jako aktuální řetězec.

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
