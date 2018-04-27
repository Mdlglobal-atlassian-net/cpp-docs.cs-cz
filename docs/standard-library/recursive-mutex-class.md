---
title: recursive_mutex – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
dev_langs:
- C++
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: 277577fc8a126a23d9531de2a7c87cdb4b0bc673
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="recursivemutex-class"></a>recursive_mutex – třída

Představuje *mutex typu*. Rozdíl k [mutex](../standard-library/mutex-class-stl.md), je dobře definovaný chování volání uzamčení metod pro objekty, které jsou již uzamčena.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Vytvoří `recursive_mutex` objektu.|
|[~recursive_mutex Destructor](#dtorrecursive_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `recursive_mutex` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Volající vlákno zablokuje, dokud vlákno získá vlastnictví mutex.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví mutex bez blokování.|
|[odemknutí](#unlock)|Uvolní vlastnictví mutex.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mutex >

**Namespace:** – std

## <a name="lock"></a>  Zámek

Blokuje volající vlákno, dokud vlákno získá vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, vrátí tato metoda hodnotu okamžitě a předchozí zámek zůstává v platnosti.

## <a name="recursive_mutex"></a>  recursive_mutex

Vytvoří `recursive_mutex` objekt, který není uzamčený.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>  ~ recursive_mutex

Uvolní všechny prostředky, které jsou používány objektu.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud při spuštění destruktoru, není objekt uzamčen, chování nedefinovaný.

## <a name="try_lock"></a>  try_lock –

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud metoda úspěšně získá vlastnictví `mutex` nebo pokud již vlastní volající vlákno `mutex`, jinak hodnota `false`.

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, funkce hned vrátí `true`, a předchozí zámek zůstává v platnosti.

## <a name="unlock"></a>  odemknutí

Uvolní vlastnictví mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda uvolní vlastnictví `mutex` až po jako tolikrát, kolikrát se označuje jako [zámku](#lock) a [try_lock –](#try_lock) byla úspěšně volána na `recursive_mutex` objektu.

Pokud není vlastníkem volající vlákno `mutex`, chování není definován.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex >](../standard-library/mutex.md)<br/>
