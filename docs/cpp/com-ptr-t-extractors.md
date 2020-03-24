---
title: _com_ptr_t – extraktory
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: 31ac39104c041d1d119f6cd06de5f9c4a620dac0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190024"
---
# <a name="_com_ptr_t-extractors"></a>_com_ptr_t – extraktory

**Specifické pro společnost Microsoft**

Extrahuje zapouzdřený ukazatel rozhraní COM.

## <a name="syntax"></a>Syntaxe

```
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>Poznámky

- **operátor rozhraní** <strong>\*</strong> vrátí zapouzdřený ukazatel rozhraní, který může mít hodnotu null.

- **operátor & rozhraní** Vrátí odkaz na zapouzdřený ukazatel rozhraní a vydá chybu, pokud má ukazatel hodnotu NULL.

- **operátor** <strong>\*</strong> umožňuje objektu inteligentního ukazatele chovat, jako by se jednalo o skutečné zapouzdřené rozhraní, když se na něj odkazuje.

- **operátor->** Umožňuje objektu inteligentního ukazatele chovat, jako by se jednalo o skutečné zapouzdřené rozhraní, když se na něj odkazuje.

- **operátor &** Uvolní libovolný zapouzdřený ukazatel rozhraní a nahradí ho hodnotou NULL a vrátí adresu zapouzdřeného ukazatele. To umožňuje, aby byl inteligentní ukazatel předán pomocí adresy funkci, která má *výstupní* parametr, prostřednictvím kterého vrací ukazatel rozhraní.

- **operátor bool** Povoluje použití objektu inteligentního ukazatele v podmíněném výrazu. Tento operátor vrátí hodnotu TRUE, pokud ukazatel nemá hodnotu NULL.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
