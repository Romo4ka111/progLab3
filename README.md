

1. Очистка build и пересборка
```
rm -rf build
mkdir build
cd build
cmake ..
make
```

2. обнуление счётчиков
```
lcov --directory . --zerocounters
```

3. Запуск тестов с отладкой
```
ctest --output-on-failure
```

4. Сбор данных с тестов (для построение общей картины тестирования)
```
lcov --capture --directory . --output-file coverage.info --ignore-errors mismatch,inconsistent,negative,empty
```
5. Фильтрация (оставить только папку с нашими структурами)
```
lcov --remove coverage.info '/usr/*' '*/_deps/*' '*/tests/*' '*/bench.cpp' --output-file coverage_cleaned.info --ignore-errors unused
```

6. Генерация html отчёта  (build/coverage_report/index.html)
```
genhtml coverage_cleaned.info --output-directory coverage_report
```

Запуск бенчмарков 
cd build -> ./bench

Запуск сереализации
cd build -> ./serialization_test
 
