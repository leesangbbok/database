```sql

--===========================================GROUP BY절 사용법
--부서번호가 있는경우만 출력
SELECT
    department_id as deparID
    , COUNT(employee_id) as 인원수
    , SUM(salary) as 월급합
FROM employees
WHERE department_id IS NOT NULL
GROUP BY department_id 
ORDER BY department_id;

-- 부서 20 50 60 80 인 사람들만 출력
SELECT
    department_id as deparID
    , COUNT(employee_id) as 인원수
    , SUM(salary) as 월급합
FROM employees
WHERE department_id IN(20, 50, 60, 80)
GROUP BY department_id 
ORDER BY department_id;

--=================================================HAVING절 사용법
-- 총계가 20000이상인 부서
-- WHERE 절에서는 집계함수를 사용 할 수 없다.
-- HAVING 절은 집계함수를 가지고 조건비교를 할 때 사용한다.
-- HAVING절은 GROUP BY절과 함께 사용이 된다.
SELECT
    department_id as 부서명
    , SUM(salary) as 총계
FROM employees
WHERE department_id IS NOT NULL
GROUP BY department_id
HAVING SUM(salary) >= 20000
ORDER BY 총계 DESC;

```