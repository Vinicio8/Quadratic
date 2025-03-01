# Quadratic
Quadratic solution

#include <iostream>

#include <cmath>

#include <utility>


std::pair<bool, std::pair<double, double>> solveQuadratic(double a, double b, double c) {
    if (a == 0) {
        if (b == 0) {
            return {false, {0, 0}}; 
        }
        double x = -c / b;
        return {true, {x, x}}; 
    }

    double discriminant = b * b - 4 * a * c;

    if (discriminant < 0) {
        return {false, {0, 0}}; 
    }

    double sqrtDiscriminant = std::sqrt(discriminant);
    double x1 = (-b + sqrtDiscriminant) / (2 * a);
    double x2 = (-b - sqrtDiscriminant) / (2 * a);

    return {true, {x1, x2}};
}

int main() {
    double a, b, c;
    std::cout << "Ingrese los coeficientes a, b y c: ";
    
    if (!(std::cin >> a >> b >> c)) {
        std::cerr << "Error: Entrada inválida. Asegúrese de ingresar números." << std::endl;
        return 1; 
    }

    auto result = solveQuadratic(a, b, c);

    if (result.first) {
        if (result.second.first == result.second.second) {
            std::cout << "La única solución es: " << result.second.first << std::endl;
        } else {
            std::cout << "Las soluciones son: " << result.second.first << " y " << result.second.second << std::endl;
        }
    } else {
        std::cout << "No hay soluciones reales." << std::endl;
    }

    return 0;
}
