---
title: "errno – konstanty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
dev_langs: C++
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fdfb4477b4de30221a0e89db02cd45178b70db0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="errno-constants"></a>errno – konstanty
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <errno.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 **Errno** hodnoty jsou konstanty přiřazené [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) v případě různé chybové stavy.  
  
 KÓD CHYBY. H obsahuje definice **errno** hodnoty. Nicméně, ne všechny definic v kód chyby. H se používají v operačních systémech Windows 32-bit. Některé hodnoty v kód chyby. H jsou k dispozici pro zachování kompatibility se systémem UNIX řady operačních systémů.  
  
 **Errno** hodnoty v operačním systému Windows 32-bit, jsou podmnožinou hodnoty **errno** v systémech XENIX. Proto **errno** hodnota není nutně stejný jako kód skutečné chyby vrácené voláním systému z operačních systémech Windows. Chcete-li získat přístup k kód chyby skutečné operačního systému, použijte [_doserrno –](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) proměnné, která obsahuje tuto hodnotu.  
  
 Následující **errno** hodnoty jsou podporovány:  
  
 **ECHILD –**  
 Žádné vytvářený procesy.  
  
 **EAGAIN –**  
 Žádné další procesy. Pokus o vytvoření nového procesu se nezdařil, protože nejsou žádné další sloty proces, nebo není dostatek paměti nebo bylo dosaženo maximální úroveň vnoření.  
  
 **E2BIG –**  
 Seznam argumentů je příliš dlouhý.  
  
 **EACCES –**  
 Bylo odepřeno oprávnění. Nastavení oprávnění souboru neumožňuje zadaný přístup. Tato chyba označuje, že byl učiněn pokus o přístup k souboru (nebo v některých případech adresář) v, které není kompatibilní s atributy souboru.  
  
 Například chybě může dojít při pokusu o čtení ze souboru, který není otevřený, otevře existující soubor jen pro čtení pro zápis nebo otevřete adresář místo souboru. V části verze operačního systému MS-DOS 3.0 a novějších **eacces –** může taky znamenat zamknutí nebo narušení sdílení.  
  
 K chybě může dojít také při pokusu o přejmenování souboru nebo adresáři nebo odebrat existující adresář.  
  
 **EBADF –**  
 Počet chybných souborů. Existují dvě možné příčiny: 1) popisovač zadaný soubor není platná hodnota nebo neodkazuje na otevření souboru. 2) byl k pokusu o zápis do souboru nebo zařízení otevřen pro čtení.  
  
 **EDEADLOCK –**  
 By k zablokování prostředků. Argument matematické funkce není v doméně funkce.  
  
 **EDOM –**  
 Matematické argument.  
  
 **EEXIST –**  
 Soubory existují. Byl proveden pokus o vytvoření souboru, který již existuje. Například **_o_creat –** a **_o_excl –** příznaky jsou určené v **_Otevřít** volání, ale soubor s názvem již existuje.  
  
 **EILSEQ –**  
 Neplatné pořadí bajtů (například v řetězci MBCS).  
  
 **EINVAL –**  
 Neplatný argument. Neplatná hodnota byl zadán pro jeden z argumentů pro funkci. Například hodnota zadána pro počátek při umístění ukazatele souboru (prostřednictvím volání **fseek**) je před začátkem souboru.  
  
 **EMFILE –**  
 Příliš mnoho souborů. Žádné další popisovače souborů jsou k dispozici, takže nelze otevřít žádné další soubory.  
  
 **ENOENT –**  
 Podobný soubor nebo adresář. Zadaný soubor nebo adresář neexistuje nebo nebyl nalezen. Tato zpráva může dojít při každém zadaný soubor neexistuje nebo součást cesty neurčuje existující adresář.  
  
 **ENOEXEC –**  
 Chyba formátu exec. Byl proveden pokus o spuštění souboru, který není spustitelný soubor nebo který má neplatný formát souboru spustitelný soubor.  
  
 **ENOMEM –**  
 Není dostatek jádra. Je k dispozici pro pokus o operátor není dostatek paměti. Například tato zpráva může dojít, když není dostatek paměti k dispozici pro spuštění podřízeného procesu, nebo když v žádosti o přidělení **_getcwd –** volání nelze uspokojit.  
  
 **ENOSPC –**  
 Není dostatek místa na zařízení. Žádné další místo pro zápis je k dispozici na zařízení (například při zaplnění disku).  
  
 **ERANGE –**  
 Výsledek je příliš velký. Argument matematické funkce je příliš velký, což vede k částečné nebo úplné ztrátě násobek ve výsledku. Této chybě může dojít také v jiných funkcí, když argument je větší, než se očekávalo (například když *vyrovnávací paměti* argument **_getcwd –** je delší, než se očekávalo).  
  
 **EXDEV –**  
 Odkaz mezi zařízeními. Byl proveden pokus o přesunete soubor na jiné zařízení (pomocí **přejmenovat** funkce).  
  
 **STRUNCATE –**  
 Řetězec kopírování nebo zřetězení výsledkem zkrácený řetězec. V tématu [_truncate –](../c-runtime-library/truncate.md).  
  
 Následující hodnoty jsou podporovány pro kompatibilitu s Posix. Jsou požadované hodnoty v systémech jiných Posix.  
  
```  
#define E2BIG [argument list too long]  
#define EACCES [permission denied]  
#define EADDRINUSE [address in use]  
#define EADDRNOTAVAIL [address not available]  
#define EAFNOSUPPORT [address family not supported]  
#define EAGAIN [resource unavailable try again]  
#define EALREADY [connection already in progress]  
#define EBADF [bad file descriptor]  
#define EBADMSG [bad message]  
#define EBUSY [device or resource busy]  
#define ECANCELED [operation canceled]  
#define ECHILD [no child process]  
#define ECONNABORTED [connection aborted]  
#define ECONNREFUSED [connection refused]  
#define ECONNRESET [connection reset]  
#define EDEADLK [resource deadlock would occur]  
#define EDESTADDRREQ [destination address required]  
#define EDOM [argument out of domain]  
#define EEXIST [file exists]  
#define EFAULT [bad address]  
#define EFBIG [file too large]  
#define EHOSTUNREACH [host unreachable]  
#define EIDRM [identifier removed]  
#define EILSEQ [illegal byte sequence]  
#define EINPROGRESS [operation in progress]  
#define EINTR [interrupted]  
#define EINVAL [invalid argument]  
#define EIO [io error]  
#define EISCONN [already connected]  
#define EISDIR [is a directory]  
#define ELOOP [too many synbolic link levels]  
#define EMFILE [too many files open]  
#define EMLINK [too many links]  
#define EMSGSIZE [message size]  
#define ENAMETOOLONG [filename too long]  
#define ENETDOWN [network down]  
#define ENETRESET [network reset]  
#define ENETUNREACH [network unreachable]  
#define ENFILE [too many files open in system]  
#define ENOBUFS [no buffer space]  
#define ENODATA [no message available]  
#define ENODEV [no such device]  
#define ENOENT [no such file or directory]  
#define ENOEXEC [executable format error]  
#define ENOLCK [no lock available]  
#define ENOLINK [no link]  
#define ENOMEM [not enough memory]  
#define ENOMSG [no message]  
#define ENOPROTOOPT [no protocol option]  
#define ENOSPC [no space on device]  
#define ENOSR [no stream resources]  
#define ENOSTR [not a stream]  
#define ENOSYS [function not supported]  
#define ENOTCONN [not connected]  
#define ENOTDIR [not a directory]  
#define ENOTEMPTY [directory not empty]  
#define ENOTRECOVERABLE [state not recoverable]  
#define ENOTSOCK [not a socket]  
#define ENOTSUP [not supported]  
#define ENOTTY [inappropriate io control operation]  
#define ENXIO [no such device or address]  
#define EOPNOTSUPP [operation not supported]  
#define EOTHER [other]  
#define EOVERFLOW [value too large]  
#define EOWNERDEAD [owner dead]  
#define EPERM [operation not permitted]  
#define EPIPE [broken pipe]  
#define EPROTO [protocol error]  
#define EPROTONOSUPPORT [protocol not supported]  
#define EPROTOTYPE [wrong protocol type]  
#define ERANGE [result out of range]  
#define EROFS [read only file system]  
#define ESPIPE [invalid seek]  
#define ESRCH [no such process]  
#define ETIME [stream timeout]  
#define ETIMEDOUT [timed out]  
#define ETXTBSY [text file busy]  
#define EWOULDBLOCK [operation would block]  
#define EXDEV [cross device link]  
```  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)