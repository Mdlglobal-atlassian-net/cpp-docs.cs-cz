---
title: 'Platform:: String – Třída'
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
ms.openlocfilehash: 3c8c179c416ca744cace26cff3def0829f425664
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587922"
---
# <a name="platformstring-class"></a>Platform:: String – Třída

Představuje sekvenční kolekci znaků Unicode, která se používá k reprezentaci textu. Další informace a příklady naleznete v tématu [strings](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterátory

Dvě funkce iterátoru, které nejsou členy třídy String, lze použít s funkcí šablony `std::for_each` pro zobrazení výčtu znaků v objektu String.

|Člen|Popis|
|------------|-----------------|
|`const char16* begin(String^ s)`|Vrátí ukazatel na začátek zadaného objektu řetězce.|
|`const char16* end(String^ s)`|Vrátí ukazatel za konec zadaného objektu řetězce.|

### <a name="members"></a>Členové

Třída String dědí z objektu a rozhraní IDisposable, IEquatable a IPrintable.

Třída String má také následující typy členů.

**Konstruktory**

|Člen|Popis|
|------------|-----------------|
|[String:: String](#ctor)|Inicializuje novou instanci třídy String.|

**Metody**

Třída String dědí metody Equals (), Finalize (), GetHashCode (), GetType (), MemberwiseClose () a ToString () z [třídy Platform:: Object](../cppcx/platform-object-class.md). Řetězec má také následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Řetězec:: begin](#begin)|Vrátí ukazatel na začátek aktuálního řetězce.|
|[Řetězec:: CompareOrdinal](#compareordinal)|Porovná dva `String` objekty vyhodnocením číselných hodnot odpovídajících znaků ve dvou řetězcových hodnotách reprezentovaných objekty.|
|[Řetězec:: Concat](#concat)|Zřetězí hodnoty dvou řetězcových objektů.|
|[Řetězec::D ATA](#data)|Vrátí ukazatel na začátek aktuálního řetězce.|
|[Řetězec::D pozice](#dispose)|Uvolňuje nebo uvolňuje prostředky.|
|[Řetězec:: end](#end)|Vrátí ukazatel za konec aktuálního řetězce.|
|[String:: Equals](#equals)|Označuje, zda je zadaný objekt stejný jako aktuální objekt.|
|[Řetězec:: GetHashCode](#gethashcode)|Vrátí kód hash této instance.|
|[String::-Empty](#isempty)|Určuje, zda je aktuální objekt řetězce prázdný.|
|[Řetězec:: IsFastPass](#isfastpass)|Určuje, zda je aktuální objekt řetězce zapojen do operace *rychlá operace Pass* . V operaci rychlého předání je počítání odkazů pozastaveno.|
|[String:: Length](#length)|Načte délku aktuálního objektu řetězce.|
|[String:: ToString](#tostring)|Vrátí objekt typu String, jehož hodnota je shodná s aktuálním řetězcem.|

**Operátory**

Třída String má následující operátory.

|Člen|Popis|
|------------|-----------------|
|[String:: operator = = – operátor](#operator-equality)|Určuje, zda dva zadané objekty řetězce mají stejnou hodnotu.|
|[operator + – operátor](#operator-plus)|Zřetězí dva objekty řetězce do nového objektu String.|
|[String:: operator > – operátor](#operator-greater-than)|Určuje, zda je hodnota jednoho objektu řetězce větší než hodnota druhého řetězcového objektu.|
|[String:: operator > = – operátor](#operator-greater-than-or-equals)|Určuje, zda je hodnota jednoho objektu řetězce větší než nebo rovna hodnotě druhého objektu řetězce.|
|[String:: operator! = – operátor](#operator-inequality)|Určuje, zda dva zadané objekty řetězce mají různé hodnoty.|
|[String:: operator < – operátor](#operator-less-than)|Určuje, zda je hodnota jednoho objektu řetězce menší než hodnota druhého řetězcového objektu.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Systém Windows 8

**Minimální podporovaný Server:** Windows Server 2012

**Obor názvů:** Platformy

**Header** vccorlib. h (zahrnuto ve výchozím nastavení)

## <a name="begin"></a>String:: begin – metoda

Vrátí ukazatel na začátek aktuálního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
char16* Begin();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek aktuálního řetězce.

## <a name="compareordinal"></a>String:: CompareOrdinal – metoda

Statická metoda, která porovnává dva `String` objekty vyhodnocením číselných hodnot odpovídajících znaků ve dvou řetězcových hodnotách reprezentovaných objekty.

### <a name="syntax"></a>Syntaxe

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt řetězce.

*str2*<br/>
Druhý objekt řetězce.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které označuje lexikální vztah mezi dvěma komparand. V následující tabulce jsou uvedeny možné návratové hodnoty.

|Hodnota|Podmínka|
|-----------|---------------|
|– 1|`str1` je menší než `str2`.|
|0,8|`str1` se rovná `str2`.|
|první|`str1` je větší než `str2`.|

## <a name="concat"></a>String:: Concat – metoda

Zřetězí hodnoty dvou řetězcových objektů.

### <a name="syntax"></a>Syntaxe

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt řetězce nebo `null`.

*str2*<br/>
Druhý objekt String nebo `null`.

### <a name="return-value"></a>Návratová hodnota

Nový objekt String ^, jehož hodnota je zřetězení hodnot `str1` a `str2`.

Pokud je `str1` `null` a `str2` není, `str1` se vrátí. Pokud je `str2` `null` a `str1` není, `str2` se vrátí. Jsou-li `str1` a `str2` `null`, je vrácen prázdný řetězec (L).

## <a name="data"></a>String::D metoda ATA

Vrátí ukazatel na začátek vyrovnávací paměti dat objektu jako pole ve stylu jazyka C `char16` (`wchar_t`) prvků.

### <a name="syntax"></a>Syntaxe

```
const char16* Data();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek `const char16` pole znaků Unicode (`char16` je definice typu `wchar_t`).

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li převést z `Platform::String^` na `wchar_t*`. Když se objekt `String` přestane mimo rozsah, ukazatel na data už není zaručený platný. Chcete-li uložit data po dobu životnosti původního objektu `String`, použijte [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) k zkopírování pole do paměti, kterou jste přidělili sami.

## <a name="dispose"></a>String::D metoda transpozice

Uvolňuje nebo uvolňuje prostředky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override void Dispose();
```

## <a name="end"></a>String:: end – metoda

Vrátí ukazatel za konec aktuálního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
char16* End();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na konec aktuálního řetězce.

### <a name="remarks"></a>Poznámky

End () vrátí hodnotu begin () + length.

## <a name="equals"></a>String:: Equals – metoda

Určuje, zda má zadaný řetězec stejnou hodnotu jako aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Objekt, který chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je `str` rovno aktuálnímu objektu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato metoda je ekvivalentní se statickým [řetězcem:: CompareOrdinal](#compareordinal). V prvním přetížení se očekává, že parametr `str` lze přetypovat na objekt typu String ^.

## <a name="gethashcode"></a>String:: GetHashCode – metoda

Vrátí kód hash této instance.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Kód hash této instance

## <a name="isempty"></a>String::-Empty – metoda

Určuje, zda je aktuální objekt řetězce prázdný.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je aktuální objekt `String` **null** nebo prázdný řetězec (L ""); v opačném případě **false**.

## <a name="isfastpass"></a>String:: IsFastPass – metoda

Určuje, zda je aktuální objekt řetězce zapojen do operace *rychlá operace Pass* . V operaci rychlého předání je počítání odkazů pozastaveno.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je aktuální objekt `String` rychlým v minulosti; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Ve volání funkce, kde je objekt počítaného odkazu parametr, a volaná funkce pouze přečte tento objekt, kompilátor může bezpečně pozastavit počítání odkazů a zvýšit výkon volání. Neexistuje žádné užitečné, aby váš kód mohl s touto vlastností dělat. Systém zpracuje všechny podrobnosti.

## <a name="length"></a>String:: Length – metoda

Načte počet znaků v aktuálním objektu `String`.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků v aktuálním objektu `String`.

### <a name="remarks"></a>Poznámky

Délka řetězce bez znaků je nula. Délka následujícího řetězce je 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Pole znaků vrácené [řetězcem::D ATA](#data) má jeden další znak, což je ukončující hodnota null nebo \ 0. Tento znak je také dlouhý dva bajty.

## <a name="operator-plus"></a>String:: operator + – operátor

Zřetězí dva objekty [řetězce](../cppcx/platform-string-class.md) do nového objektu [String](../cppcx/platform-string-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt `String`.

*str2*<br/>
Druhý objekt `String`, jehož obsah bude přidán do `str1`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je *str1* rovno *str2*; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento operátor vytvoří objekt `String^`, který obsahuje data z obou operandů. Využijte ji pro pohodlí, pokud extrémní výkon není kritický. Několik volání "`+`" ve funkci pravděpodobně nebude patrné, ale pokud pracujete s velkými objekty nebo textovými daty v těsné smyčce, pak použijte standardní C++ mechanismy a typy.

##  <a name="operator-equality"></a>String:: operator = = – operátor

Určuje, zda dva zadané objekty řetězce mají stejnou textovou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt `String`, který se má porovnat.

*str2*<br/>
Druhý objekt `String`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je obsah `str1` rovný `str2`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento operátor je ekvivalentní [řetězci:: CompareOrdinal](#compareordinal).

##  <a name="operator-greater-than"></a>String:: operator &gt;

Určuje, zda je hodnota jednoho `String` objektu větší než hodnota druhého objektu `String`.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt `String`.

*str2*<br/>
Druhý objekt `String`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hodnota `str1` větší než hodnota `str2`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento operátor je ekvivalentní k explicitnímu volání [řetězce:: CompareOrdinal](#compareordinal) a získání výsledku většího než nula.

## <a name="operator-greater-than-or-equals"></a>String:: operator &gt; =

Určuje, zda je hodnota jednoho `String` objektu větší nebo rovna hodnotě druhého objektu `String`.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt `String`.

*str2*<br/>
Druhý objekt `String`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hodnota `str1` větší nebo rovna hodnotě `str2`; v opačném případě **false**.

## <a name="operator-inequality"></a>String:: operator! =

Určuje, zda dva zadané `String` objekty mají jiné hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt `String`, který se má porovnat.

*str2*<br/>
Druhý objekt `String`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud `str1` není rovno `str2`; v opačném případě **false**.

## <a name="operator-less-than"></a>String:: operator &lt;

Určuje, zda je hodnota jednoho objektu `String` menší než hodnota druhého objektu `String`.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První objekt `String`.

*str2*<br/>
Druhý objekt `String`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hodnota *str1* menší než hodnota *str2*; v opačném případě **false**.

## <a name="ctor"></a>String:: String – konstruktor

Inicializuje novou instanci třídy `String` s kopií vstupních řetězcových dat.

### <a name="syntax"></a>Syntaxe

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parametry

*pracují*<br/>
Řada velkých znaků, které inicializují řetězec. Char16

*n*<br/>
Číslo, které určuje délku řetězce.

### <a name="remarks"></a>Poznámky

Pokud je výkon kritický a Vy ovládáte životnost zdrojového řetězce, můžete místo řetězce použít [Platform:: StringReference](../cppcx/platform-stringreference-class.md) .
### <a name="example"></a>Příklad

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a>String:: ToString

Vrátí objekt `String`, jehož hodnota je shodná s aktuálním řetězcem.

### <a name="syntax"></a>Syntaxe

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `String`, jehož hodnota je shodná s aktuálním řetězcem.

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
