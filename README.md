class BMICalculator {
  final double height; // in cm
  final double weight; // in kg

  BMICalculator({required this.height, required this.weight});

  double calculateBMI() {
    final h = height / 100;
    return weight / (h * h);
  }

  String getCategory(double bmi) {
    if (bmi < 18.5) return "Underweight";
    if (bmi < 24.9) return "Normal";
    if (bmi < 29.9) return "Overweight";
    return "Obese";
  }

  String getHealthTip(String category) {
    switch (category) {
      case "Underweight":
        return "Try to gain weight with healthy calories.";
      case "Normal":
        return "Great job! Keep maintaining your lifestyle.";
      case "Overweight":
        return "Consider more physical activity and a balanced diet.";
      case "Obese":
        return "It's important to seek medical advice and a fitness plan.";
      default:
        return "";
    }
  }
}
import 'bmi_calculator.dart';
import 'bmi_result_screen.dart';

void _calculateAndNavigate() {
  final calculator = BMICalculator(height: height, weight: weight);
  final bmi = calculator.calculateBMI();

  Navigator.push(
    context,
    MaterialPageRoute(
      builder: (context) => BMIResultScreen(bmi: bmi),
    ),
  );
}
