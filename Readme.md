1. SELECT \* FROM "students" a
   JOIN "classes" b ON a.class_id = b.id
   JOIN "teachers" c ON b.teacher_id = c.id;

2. SELECT \* FROM "teachers" a
   JOIN "classes" b ON a.id = b.teacher_id;

3. CREATE VIEW student_class_teacher AS
   SELECT a.name as student_name, b.name as class_name, c.name as teacher_name FROM "students" a
   JOIN "classes" b ON a.class_id = b.id
   JOIN "teachers" c ON b.teacher_id = c.id;

4. CREATE OR REPLACE FUNCTION fx()
   RETURNS SETOF "classes" AS $$
BEGIN
  RETURN QUERY SELECT * FROM "classes";
END
$$ LANGUAGE plpgsql;

SELECT \* FROM fx();
