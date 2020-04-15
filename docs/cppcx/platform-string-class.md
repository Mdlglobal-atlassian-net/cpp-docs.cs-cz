---
title: Platforma::Třída řetězce
ms.date: 10/16/2019
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
ms.openlocfilehash: 3f29c60d0d6a4618d97d8f750a048fcc18f976b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322117"
---
# <a name="platformstring-class"></a>Platforma::Třída řetězce

Představuje sekvenční kolekci znaků Unicode, která se používá k reprezentaci textu. Další informace a příklady naleznete v tématu [Řetězce](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterátory

Dvě iterátorové funkce, které nejsou členy třídy String, `std::for_each` lze použít s funkcí šablony k vytvoření výčtu znaků znaků v objektu String.

|Člen|Popis|
|------------|-----------------|
|`const char16* begin(String^ s)`|Vrátí ukazatel na začátek zadaného objektu String.|
|`const char16* end(String^ s)`|Vrátí ukazatel za konec zadaného objektu String.|

## <a name="members"></a>Členové

String třída dědí z Object a IDisposable, IEquatable a IPrintable rozhraní.

Třída String má také následující typy členů.

### <a name="constructors"></a>Konstruktory

|Člen|Popis|
|------------|-----------------|
|[Řetězec::Řetězec](#ctor)|Inicializuje novou instanci třídy String.|

### <a name="methods"></a>Metody

Třída String zdědí metody Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose(), a ToString() z [třídy Platform::Object .](../cppcx/platform-object-class.md) Řetězec má také následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Řetězec::Začátek](#begin)|Vrátí ukazatel na začátek aktuálního řetězce.|
|[Řetězec::PorovnatOrdinální](#compareordinal)|Porovná dva `String` objekty vyhodnocením číselných hodnot odpovídajících znaků ve dvou řetězcových hodnotách reprezentovanéobjekty.|
|[Řetězec::Concat](#concat)|Zřetězí hodnoty dvou objektů String.|
|[Řetězec::Data](#data)|Vrátí ukazatel na začátek aktuálního řetězce.|
|[Řetězec::Dispose](#dispose)|Uvolní nebo uvolní prostředky.|
|[Řetězec::Konec](#end)|Vrátí ukazatel za konec aktuálního řetězce.|
|[Řetězec::Rovná se](#equals)|Označuje, zda je zadaný objekt roven aktuálnímu objektu.|
|[Řetězec::GetHashCode](#gethashcode)|Vrátí hodnotu hash pro tuto instanci.|
|[Řetězec::IsEmpty](#isempty)|Označuje, zda je aktuální objekt String prázdný.|
|[Řetězec::IsfastPass](#isfastpass)|Označuje, zda se aktuální objekt String účastní operace *rychlého průchodu.* Při operaci rychlého průchodu je počítání odkazů pozastaveno.|
|[Řetězec::Délka](#length)|Načte délku aktuálního objektu String.|
|[Řetězec::ToString](#tostring)|Vrátí objekt String, jehož hodnota je stejná jako aktuální řetězec.|

### <a name="operators"></a>Operátory

Třída String má následující operátory.

|Člen|Popis|
|------------|-----------------|
|[Řetězec::operator== Operátor](#operator-equality)|Označuje, zda mají dva zadané objekty String stejnou hodnotu.|
|[operátor+ Operátor](#operator-plus)|Zřetězí dva objekty String do nového objektu String.|
|[Řetězec::operátor> operátor](#operator-greater-than)|Označuje, zda je hodnota jednoho objektu String větší než hodnota druhého objektu String.|
|[Řetězec::operátor>= Operátor](#operator-greater-than-or-equals)|Označuje, zda je hodnota jednoho objektu String větší nebo rovna hodnotě druhého objektu String.|
|[Řetězec::operátor!= Operátor](#operator-inequality)|Označuje, zda mají dva zadané objekty String různé hodnoty.|
|[Řetězec::operátor< operátor](#operator-less-than)|Označuje, zda je hodnota jednoho objektu String menší než hodnota druhého objektu String.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Záhlaví** vccorlib.h (ve výchozím nastavení zahrnuto)

## <a name="stringbegin-method"></a><a name="begin"></a>Řetězec::Begin Metoda

Vrátí ukazatel na začátek aktuálního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
char16* Begin();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek aktuálního řetězce.

## <a name="stringcompareordinal-method"></a><a name="compareordinal"></a>Řetězec::CompareOrdinal metoda

Statická metoda, `String` která porovnává dva objekty vyhodnocením číselných hodnot odpovídajících znaků ve dvou řetězcových hodnotách reprezentovanéobjekty.

### <a name="syntax"></a>Syntaxe

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První String objekt.

*str2*<br/>
Druhý String objekt.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které označuje lexikální vztah mezi dvěma comparands. V následující tabulce jsou uvedeny možné vrácené hodnoty.

|Hodnota|Podmínka|
|-----------|---------------|
|-1|`str1`je menší `str2`než .|
|0|`str1`je rovna `str2`.|
|1|`str1`je větší `str2`než .|

## <a name="stringconcat-method"></a><a name="concat"></a>Řetězec::Metoda Concat

Zřetězí hodnoty dvou objektů String.

### <a name="syntax"></a>Syntaxe

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První String objekt, `null`nebo .

*str2*<br/>
Druhý String objekt `null`nebo .

### <a name="return-value"></a>Návratová hodnota

Nový String^ objekt, jehož hodnota je zřetězení hodnoty `str1` a `str2`.

Pokud `str1` `null` je `str2` a `str1` není, je vrácena. Pokud `str2` `null` je `str1` a `str2` není, je vrácena. Pokud `str1` `str2` a `null`jsou obojí , je vrácen prázdný řetězec (L").

## <a name="stringdata-method"></a><a name="data"></a>String::Data Metoda

Vrátí ukazatel na začátek vyrovnávací paměti dat objektu jako `char16` pole`wchar_t`elementů ve stylu C .

### <a name="syntax"></a>Syntaxe

```cpp
const char16* Data();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek `const char16` pole znaků Unicode`char16` ( je `wchar_t`typedef pro ).

### <a name="remarks"></a>Poznámky

Tuto metodu použijte `Platform::String^` `wchar_t*`k převodu z do . Když `String` objekt přejde mimo rozsah, ukazatel data již není zaručeno, že je platný. Chcete-li data uložit i `String` po uplynutí doby životnosti původního objektu, použijte [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) zkopírovat pole do paměti, kterou jste sami přidělili.

## <a name="stringdispose-method"></a><a name="dispose"></a>String::Dispose Metoda

Uvolní nebo uvolní prostředky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override void Dispose();
```

## <a name="stringend-method"></a><a name="end"></a>Řetězec::Endmetoda

Vrátí ukazatel za konec aktuálního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
char16* End();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na konec aktuálního řetězce.

### <a name="remarks"></a>Poznámky

End() vrátí Begin() + Length.

## <a name="stringequals-method"></a><a name="equals"></a>Řetězec::Metoda rovná se

Označuje, zda zadaný řetězec má stejnou hodnotu jako aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Objekt k porovnání

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `str` se rovná aktuálnímu objektu; jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda je ekvivalentní statické [String::CompareOrdinal](#compareordinal). V prvním přetížení se očekává, že `str` parametr může být přetypován string^ objektu.

## <a name="stringgethashcode-method"></a><a name="gethashcode"></a>String::Metoda GetHashCode

Vrátí hodnotu hash pro tuto instanci.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Kód hash této instance

## <a name="stringisempty-method"></a><a name="isempty"></a>Řetězec::IsEmpty Metoda

Označuje, zda je aktuální objekt String prázdný.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `String` je aktuální objekt **null** nebo prázdný řetězec (L""); jinak **false**.

## <a name="stringisfastpass-method"></a><a name="isfastpass"></a>String::Metoda isfastpass

Označuje, zda se aktuální objekt String účastní operace *rychlého průchodu.* Při operaci rychlého průchodu je počítání odkazů pozastaveno.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `String` je aktuální objekt rychle minulostí; jinak **false**.

### <a name="remarks"></a>Poznámky

Při volání funkce, kde odkaz počítal objekt je parametr a volaná funkce pouze čte tento objekt, kompilátor může bezpečně pozastavit počítání odkazů a zlepšit výkon volání. Není nic užitečného, co váš kód může dělat s touto vlastností. Systém zpracovává všechny detaily.

## <a name="stringlength-method"></a><a name="length"></a>Řetězec::Metoda délky

Načte počet znaků v `String` aktuálním objektu.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků v aktuálním `String` objektu.

### <a name="remarks"></a>Poznámky

Délka String bez znaků je nula. Délka následujícího řetězce je 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Pole znaků vrácené [string::Data](#data) má jeden další znak, což je ukončující null nebo '\0'. Tento znak je také dlouhý dva bajty.

## <a name="stringoperator-operator"></a><a name="operator-plus"></a>Řetězec::operátor+ operátor

Zřetězí dva objekty [String](../cppcx/platform-string-class.md) do nového objektu [String.](../cppcx/platform-string-class.md)

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt.

*str2*<br/>
Druhý `String` objekt, jehož obsah bude `str1`připojen k aplikaci .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *str1* se rovná *str2*; jinak **false**.

### <a name="remarks"></a>Poznámky

Tento operátor `String^` vytvoří objekt, který obsahuje data ze dvou operandů. Použijte jej pro pohodlí, když extrémní výkon není rozhodující. Několik volání "`+`" ve funkci pravděpodobně nebude patrné, ale pokud manipulujete s velkými objekty nebo textovými daty v těsné smyčce, použijte standardní mechanismy a typy jazyka C++.

## <a name="stringoperator-operator"></a><a name="operator-equality"></a>Řetězec::operator== Operátor

Označuje, zda mají dva zadané objekty String stejnou textovou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt porovnat.

*str2*<br/>
Druhý `String` objekt porovnat.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `str1` je obsah `str2`rovny ; jinak **false**.

### <a name="remarks"></a>Poznámky

Tento operátor je ekvivalentní [String::CompareOrdinal](#compareordinal).

## <a name="stringoperatorgt"></a><a name="operator-greater-than"></a>Řetězec::operátor&gt;

Označuje, zda je `String` hodnota jednoho objektu větší `String` než hodnota druhého objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt.

*str2*<br/>
Druhý `String` objekt.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `str1` je hodnota vyšší `str2`než hodnota ; jinak **false**.

### <a name="remarks"></a>Poznámky

Tento operátor je ekvivalentní explicitně volat [String::CompareOrdinal](#compareordinal) a získání výsledku větší než nula.

## <a name="stringoperatorgt"></a><a name="operator-greater-than-or-equals"></a>Řetězec::operátor&gt;=

Označuje, zda je `String` hodnota jednoho objektu větší nebo `String` rovna hodnotě druhého objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt.

*str2*<br/>
Druhý `String` objekt.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `str1` je hodnota vyšší nebo rovna hodnotě `str2`; jinak **false**.

## <a name="stringoperator"></a><a name="operator-inequality"></a>Řetězec::operátor!=

Označuje, zda `String` mají dva zadané objekty různé hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt porovnat.

*str2*<br/>
Druhý `String` objekt porovnat.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `str1` se `str2`nerovná ; jinak **false**.

## <a name="stringoperatorlt"></a><a name="operator-less-than"></a>Řetězec::operátor&lt;

Označuje, zda je `String` hodnota jednoho objektu menší `String` než hodnota druhého objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První `String` objekt.

*str2*<br/>
Druhý `String` objekt.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je hodnota *str1* menší než hodnota *str2*; jinak **false**.

## <a name="stringstring-constructor"></a><a name="ctor"></a>Řetězec::Konstruktor řetězce

Inicializuje novou instanci `String` třídy s kopií dat vstupního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parametry

*S*<br/>
Řada širokých znaků, které inicializují řetězec. znak16

*N*<br/>
Číslo, které určuje délku řetězce.

### <a name="remarks"></a>Poznámky

Pokud je výkon kritický a řídíte životnost zdrojového řetězce, můžete místo String použít [platformu::StringReference.](../cppcx/platform-stringreference-class.md)

### <a name="example"></a>Příklad

```cpp
String^ s = L"Hello!";
```

## <a name="stringtostring"></a><a name="tostring"></a>Řetězec::ToString

Vrátí `String` objekt, jehož hodnota je stejná jako aktuální řetězec.

### <a name="syntax"></a>Syntaxe

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `String` jehož hodnota je stejná jako aktuální řetězec.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
