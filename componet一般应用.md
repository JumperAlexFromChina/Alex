* component_add
* componet_match_add
* component_master_add_with_match
---
* component_match中的compare.fn和compare.data的顺序，决定了component_master_add_child中将component加入master->components链表的顺序，从而决定后续执行各个component.bind的顺序
* 因此，各个device执行component_match_add的顺序，就决定了component.bind的执行顺序；
* 而各个device执行component_match_add的顺序，又通常由代码中对dts的of_device_id Table决定，所以这个table中各device node的顺序，就决定了.bind的执行顺序
