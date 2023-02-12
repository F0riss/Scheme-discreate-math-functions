# scheme program 
;this is a sheme program the has the following functions subset, union, intersection, difference 

(define (member x set)
(cond
((null? set) #F )
((equal? x (car set)) #T)
(else (member x (cdr set)))
))

(define (subset s1 s2)
  (cond
    ((equal? s1 s2) #T)
    ((< (length s2) (length s1))#F);there is no way s1.length can be > than s2.length and still be a subset
    ;((>(car s1) (car s2))#F)
    ((null? s1)#t)
 ((member (car s1) s2)(subset  (cdr s1) s2))
 (else #F)
   
    ))

(subset '(a c) '(a b c d))

(define (intersection list1 list2)
  (cond ((or (null? list1) (null? list2)) '())
        ((member (car list1) list2) (cons (car list1) (intersection (cdr list1) list2)))
        (else (intersection (cdr list1) list2))))

(intersection '(a b c) '(a c d))


(define (difference list1 list2)
  (cond ((null? list1) '())
        ((member (car list1) list2) (difference (cdr list1) list2))
        (else (cons (car list1) (difference (cdr list1) list2)))))

(difference '(a b c) '(a c))

(define (union list1 list2)
  (cond ((null? list1) list2);checks if l1 is null if so then print l2
        ((member (car list1) list2) (union (cdr list1) list2))

        (else (cons (car list1) (union (cdr list1) list2)))))

(union '(a b c) '(a b d))
