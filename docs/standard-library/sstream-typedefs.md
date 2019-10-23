---
title: '&lt;sstream &gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::istringstream
- iosfwd/std::ostringstream
- iosfwd/std::stringbuf
- iosfwd/std::stringstream
- iosfwd/std::wistringstream
- iosfwd/std::wostringstream
- iosfwd/std::wstringbuf
- iosfwd/std::wstringstream
ms.assetid: d102edd2-ecea-4a35-a398-cf96e58dd422
ms.openlocfilehash: e8f5a20b976d196090ac9300510044e84470c462
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686285"
---
# <a name="ltsstreamgt-typedefs"></a>&lt;sstream &gt; definice typedef

||||
|-|-|-|
|[istringstream –](#istringstream)|[ostringstream –](#ostringstream)|[stringbuf –](#stringbuf)|
|[stringstream](#stringstream)|[wistringstream –](#wistringstream)|[wostringstream –](#wostringstream)|
|[wstringbuf –](#wstringbuf)|[wstringstream –](#wstringstream)|

## <a name="istringstream"></a>istringstream –

Vytvoří typ `basic_istringstream` specializované na parametr **znak** šablony.

```cpp
typedef basic_istringstream<char> istringstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_istringstream](../standard-library/basic-istringstream-class.md)specializované pro prvky typu **char**.

## <a name="ostringstream"></a>ostringstream –

Vytvoří typ `basic_ostringstream` specializované na parametr **znak** šablony.

```cpp
typedef basic_ostringstream<char> ostringstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ostringstream](../standard-library/basic-ostringstream-class.md)specializované pro prvky typu **char**.

## <a name="stringbuf"></a>stringbuf –

Vytvoří typ `basic_stringbuf` specializované na parametr **znak** šablony.

```cpp
typedef basic_stringbuf<char> stringbuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)specializované pro prvky typu **char**.

## <a name="stringstream"></a>stringstream

Vytvoří typ `basic_stringstream` specializované na parametr **znak** šablony.

```cpp
typedef basic_stringstream<char> stringstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_stringstream](../standard-library/basic-stringstream-class.md)specializované pro prvky typu **char**.

## <a name="wistringstream"></a>wistringstream –

Vytvoří typ `basic_istringstream` specializované na parametr šablony **wchar_t** .

```cpp
typedef basic_istringstream<wchar_t> wistringstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_istringstream](../standard-library/basic-istringstream-class.md)specializované pro prvky typu **wchar_t**.

## <a name="wostringstream"></a>wostringstream –

Vytvoří typ `basic_ostringstream` specializované na parametr šablony **wchar_t** .

```cpp
typedef basic_ostringstream<wchar_t> wostringstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ostringstream](../standard-library/basic-ostringstream-class.md)specializované pro prvky typu **wchar_t**.

## <a name="wstringbuf"></a>wstringbuf –

Vytvoří typ `basic_stringbuf` specializované na parametr šablony **wchar_t** .

```cpp
typedef basic_stringbuf<wchar_t> wstringbuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)specializované pro prvky typu **wchar_t**.

## <a name="wstringstream"></a>wstringstream –

Vytvoří typ `basic_stringstream` specializované na parametr šablony **wchar_t** .

```cpp
typedef basic_stringstream<wchar_t> wstringstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_stringstream](../standard-library/basic-stringstream-class.md)specializované pro prvky typu **wchar_t**.

## <a name="see-also"></a>Viz také:

[\<sstream >](../standard-library/sstream.md)
