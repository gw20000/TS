TS-5-bit enum type

eg:

enum Permission {

               read,
               write,
              create,
              delete

}

1.  how to combine a certain permission with another

let p: Permission = Permission.read | Permission.write

2.  how to judge whether a permission includes a certain permission

function hasSpecifiedPermission(target:Permission, per:Permission){

             return  (target & per ) === per

}

hasSpecifiedPermission(p,Permission.write) // expected output : true

3.  how to delete a permission

function deleteSpecifiedPermission(target:Permission, per:Permission){

    return    target ^ per

}

deleteSpecifiedPermission(p,Permission.write)

hasSpecifiedPermission(p,Permission.write) // expected output : false
